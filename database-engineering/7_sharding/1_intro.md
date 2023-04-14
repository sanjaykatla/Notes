# Sharding
> Sharding is a process of splitting the large table
into smaller partitions across multiple DB servers.

### Pros
* Scalability
  * Data
  * Memory
* Security (users can access certain shards)
* Optimal and smaller index size

### Cons
* Complex client
* Transactions across shards
* Rollbacks
* Schema changes are hard
* Joins
* Has to be something you know in the query