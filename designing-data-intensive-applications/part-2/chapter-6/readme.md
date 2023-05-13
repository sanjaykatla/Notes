# Chapter 6. Partitioning
### Replication
Having multiple copies of same data on multiple nodes.

### Partitioning
However Replication is not enough for very large data sets, or
for very high throughput this is not sufficient.
We need to break the data up into multiple partitions are also sharing sharding.


| Terminology     | Databases                             |
|:----------------|:--------------------------------------| 
| Shard           | MongoDB, ElasticSearch, and SolrCloud |
| Region          | HBase                                 |
| Tablet          | Bigtable                              |
| V-Node          | Cassandra, Riak                       |
| vBucket         | CouchBase                             |


Each partition is a small database on its own.

## Why Paritioning?
* Scalability

### 1. Partitioning and Replicaiton
### 2. Partitioning of Key-Value data
* Partition By Key Range
* Partition By Hash of Key
* Skewed Workloads and Relieving Hot Spots

### 3. Partitioning and secondary Indexes
### 4. Rebalancing Partitions
### 5. Request Routing