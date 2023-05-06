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

## Setting Up New Followers
* You could make the files on disk consistent by locking the database 
(making it unavailable for writes), but that would go against our goal of high availability

### Steps
1. Take snapshot from master
2. Copy snapshot to slave
3. Salve requests master from the snapshot time
4. Once catch up, slave accepts live stream from master.


## Handling Node Outages

### Follower failure: Catch-up recovery
* The follower can recover quite easily: from its log, it knows the last transaction that was processed before the fault occurred.
* Thus, the follower can connect to the leader and request all the data changes that occurred during the time when the follower was disconnected

### Leader failure: Failover
Handling a failure of the leader is trickier: one of the followers needs to
be promoted to be the new leader, clients need to be reconfigured to 
send their writes to the new leader, and the other followers need to start 
consuming data changes from the new leader. This process is called failover.

#### Automatic Failover
1. Determining that the leader has failed
2. Choosing a new leader
3. Reconfiguring the system to use the new leader

### Failover is fraught with things that can go wrong:
1. If asynchronous replication is used, the new leader may not have
received all the updates
2. Discarding writes from old leader
3. Split brain
4. Timeout period

## Implementation of Replication Logs
How does leader-based replication work under the hood?

### 1. Statement-based replication
* The leader logs every write request, and sends statements log to followers

#### Cons
* Using Now() / Random() functions
* If statements use an autoincrementing column
* SPs, triggers

```
Statement-based replication was used in MySQL before version 5.1. It is still 
sometimes used today, as it is quite compact, but by default MySQL now 
switches to row-based replication (discussed shortly) if there is any
nondeterminism in a statement
```

### 2. Write-ahead log (WAL) shipping

```
This method of replication is used in PostgreSQL and Oracle, among others
```


#### Cons

The main disadvantage is that the log describes the data on a very low level: a
WAL contains details of which bytes were changed in which disk blocks.
This makes replication closely coupled to the storage engine

### 3. Logical (row-based) log replication

```
An alternative is to use different log formats for replication and for the 
storage engine, which allows the replication log to be decoupled from the 
storage engine internals. This kind of replication log is called a logical log,
to distinguish it from the storage engine’s (physical) data representation
```

### 4. Trigger-based replication
* Application layer based replication
* Some tools, such as Oracle GoldenGate [19], can make data changes 
available to an application by reading the database log. 
* An alternative is to use features that are available in many
relational databases: triggers and stored procedures.

