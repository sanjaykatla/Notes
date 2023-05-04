# Data Structure that power your DB

Consider the world’s simplest database, implemented as two Bash functions:
```agsl
db_set () {
    echo "$1,$2" >> database
}

db_get () {
    grep "^$1," database | sed -e "s/^$1,//" | tail -n 1
}
```

The underlying storage format is very simple Key-value store.
## Key-value Store
* Write the key value to the file separated by a Comma (just like CSV)
* Keep appending the new values for updates
* This has very very good performance for something that is
so simple as appending to a file very fast
* And get function is terribly bad
* Below techniques can be used to make the retrieval fast

## Index
* In order to efficiently find the value for a particular key in the database,
we need a different data structure
* The general idea behind them is to keep some additional metadata on the side, which acts as a signpost
and helps you to locate the data you want
* An index is an additional structure that is derived from the primary data

## Hash Index
* Very similar to dictionary type data structure.
* And usually implemeted using hashmap
* Keep an in-memory hash map where every key is mapped to a byte offset in the data file—the location
at which the value can be found
* Update the byte offset when there is a key value update
* In fact this is what is **Bitcask**, the default storage
engine in **Raik**.

### We only ever append to a file—so how do we avoid eventually running out of disk space?
* A good solution is to break the log into segments of certain
size.
* We can perform compaction 
* Compaction means throwing away duplicate keys in the log, and keeping only the most 
recent update for each key.
* Each segment now has its own in-memory hash table
* We can also merge several segments together at the same time as performing the compaction
* Segments are never modified after they have been written, so the merged segment is written to a new file
* In order to find the value for a key, we first check the 
most recent segment’s hash map; if the key is not present
we check the second-most-recent segment, and so on. 
* The merging process keeps the number of segments small, 
so lookups don’t need to check many hash maps

#### File format
CSV is not the best format for a log. It’s faster and simpler to use a
binary format that first encodes the length of a string in bytes,
followed by the raw string (without need for escaping).

#### Deleting records
If you want to delete a key and its associated value, you have to append a 
special deletion record to the data file (sometimes called a tombstone). 
When log segments are merged, the tombstone tells the merging process
to discard any previous values for the deleted key.

#### Crash recovery
* If the database is restarted, the in-memory hash maps are lost. 
* In principle, you can restore each segment’s hash map by reading the 
entire segment file from beginning to end and noting the offset of the
most recent value for every key as you go along. However, 
that might take a long time if the segment files are large, 
which would make server restarts painful. 
* Bitcask speeds up recovery by storing a snapshot of each segment’s hash map 
on disk, which can be loaded into memory more quickly

#### Concurrency control
* As writes are appended to the log in a strictly sequential order, 
a common implementation choice is to have only one writer thread

### Pros
* Appending sequential which is fast
* Concurrency and crash recovery

### Cons
* Range based queries suck
* Map should fit in memory

## SSTables
* SST - Sorted String Tables 
* Small change to the segment file, that all the keys must be
  stored in order 

### Advantages:
* Merging segments is simple and efficient
* In order to find a particular key in the file, you no longer need to keep an index of all the keys in memory
* We still need an in-memory index to tell you the 
offsets for some of the keys, but it can be sparse: 
one key for every few kilobytes of segment file is 
sufficient, because a few kilobytes can be scanned 
very quickly

### Constructing and maintaining SSTables
* Maintaining a sorted structure on disk is possible 
(see “B-Trees”), but maintaining it in memory is much easier.
* There are plenty of well-known tree data structures 
that you can use, such as red-black trees or AVL trees [2].
* With these data structures, you can insert keys in any
order and read them back in sorted order
* We can now make our storage engine work as follows:

#### Mem-table
* When a write comes in, add it to an in-memory balanced tree data structure (for example, a red-black tree). 
This in-memory tree is sometimes called a memtable.
* When the memtable gets bigger than some threshold—typically a 
few megabytes—write it out to disk as an SSTable file.
* This can be done efficiently because the tree already maintains the key-value pairs
sorted by key. 
* The new SSTable file becomes the most recent segment of the database
* While the SSTable is being written out to disk, writes can continue to a new memtable instance

#### Cons
* It only suffers from one problem: if the database crashes, the most recent writes (which are in th
e memtable but not yet written out to disk) are lost
  * In order to avoid that problem, we can keep a separate log on disk to which every write is 
  immediately appended, just like in the previous section. 
  * That log is not in sorted order, but that doesn’t matter, because its only purpose is to restore the 
  memtable after a crash

## Making an LSM-tree out of SSTables
* The algorithm described here is essentially what is used in LevelDB [6] and RocksDB
* Storage engines that are based on this principle of merging and compacting sorted files are often called LSM storage engines
* 