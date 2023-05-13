# Partitioning of Key-Value Data

### Skewed Paritioning
If the partitioning is unfair, so that some partitions have more data or queries than others,
we call it skewed

### Hotspot
A partition with disproportionately high load is called a hot spot.

### How to avoid skewed data
The simplest approach to avoid skewed data is assign the data randomly.

Cons:
* when we try to read the data, we do not have any idea about there is data  stored.
* We end up searching all partitions

## Partitioning by Key Range

One way of partitioning is to assign continuous rangeof keys.

* The ranges of keys not necessarily evenly spaced.
* This paritioning strategy is used by Bigtable, its open source equivalent HBase,
RethinkDB, and MongoDB

## Partitioning by Hash of Key

Because of the risk of Skewed data and hotspots, many applications chooses a hash
function to determine the partition for a given key.

MongoDB uses MD5, Cassandra uses Murmur3, and Voldemort uses the Fowler–Noll–Vo function

* Once we have suitable hash function for keys we can assign range of hashes for
each partition.
* The partition boundaries are evenly spaced, or they can be chosen pseudorandomly

## Consistent Hashing
* Defined by Karger et al.
* It uses randomly chosen partition boundaries to avoid the need of central control

Cons:
* Unfortunately however, by using the hash of the key for partitioning 
we lose a nice property of key-range partitioning: 
the ability to do efficient range queries
* Now the range queries has to be sent to all partitions.
* Range queries on the primary key are not supported by Riak [9], Couchbase [10], or Voldemort

## Skewed Workloads and Relieving Hot Spots

