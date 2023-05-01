# Data Structure that power your DB

## Key-value Store
* Write the key value to the file
* Keep appending the new values or updates
* Below techniques can be used to make the retrieval fast

## Hash Index
* Keep an in-memory hash map where every key is mapped to a byte offset in the data file—the location
at which the value can be found
* Update the byte offset when there is a key value update
* In fact this is what is Bitcask, the default storage
engine in Raik.

### We only ever append to a file—so how do we avoid eventually running out of disk space?
* A good solution is to break the log into segments of certain
size.
* We can perform compaction 
* Compaction means throwing away duplicate keys in the log, and keeping only the most 
recent update for each key.
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
* It only suffers from one problem: if the database crashes, the most recent writes (which are in th
e memtable but not yet written out to disk) are lost

## Making an LSM-tree out of SSTables
* The algorithm described here is essentially what is used in LevelDB [6] and RocksDB
* Storage engines that are based on this principle of merging and compacting sorted files are often called LSM storage engines
* 