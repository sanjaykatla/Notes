# Rebalancing Partitions

## Strategies for Rebalancing

### 0. How not to do it: hash mod N
We need an approach that doesn’t move data around more than necessary.

The problem with the mod N approach is that if the number of nodes N changes,
most of the keys will need to be moved from one node to another

### 1. Fixed number of partitions
* Create many more partitions than there are nodes, and assign several
partitions to each node
* Only entire partitions are moved between nodes. The number of partitions does not change,
nor does the assignment of keys to partitions
* This approach to rebalancing is used in Riak [15], Elasticsearch [24], Couchbase [10], 
and Voldemort [25].
* However, each partition also has management overhead, so it’s counterproductive
to choose too high a number

### 2. Dynamic partitioning
* An advantage of dynamic partitioning is that the number of partitions 
adapts to the total data volume
* Pre-splitting to avoid initial load on one partition / node.


### 3. Partitioning proportionally to nodes
* In both of the above cases, the number of partitions is independent of
the number of nodes.
* A third option, used by Cassandra and Ketama, is to make the number of partitions proportional
to the number of nodes
* (in Cassandra, 256 partitions per node by default)

### Operations: Automatic or Manual Rebalancing
* it can be a good thing to have a human in the loop for rebalancing. It’s slower
than a fully automatic process, but it can help prevent operational surprises.

