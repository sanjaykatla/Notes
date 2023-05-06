# Leaders and Followers

```
The major difference between a thing that might go wrong and a thing that 
cannot possibly go wrong is that when a thing that cannot possibly go
wrong goes wrong it usually turns out to be impossible to get at or repair.

- Douglas Adams, Mostly Harmless (1992)
```

Replication means keeping a copy of the same data on multiple machines that are connected via a network

### Why we need to replicate the data

1. To keep data geographically close to your users (and thus reduce access latency)
2. To allow the system to continue working even if some of its parts have failed (and thus increase availability)
3. To scale out the number of machines that can serve read queries (and thus increase read throughput)

### Algorithms to Replicate Data
Three popular algorithms for replicating changes between nodes.
1. single-leader
2. multi-leader
3. leaderless

Each Node that store copy of a database is called replica.
* Also known as master/slave, active/passive replication.

1. One of the replicate designated the leader. When clients wants to write, they
must send their request to master node.
2. All other nodes are called followers. When leader node completed writing in its
local storage, it also sends this information as replication logs, or change stream.
3. When client wants to read data, it can read from leader or any of the slaves.

## Synchronous Versus Asynchronous Replication
An important detail of a replicated system is whether the replication happens 
synchronously or asynchronously. (In relational databases, this is often a 
configurable option; other systems are often hardcoded to be either one or the 
other.)



