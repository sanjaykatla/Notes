# Leaderless Replication

Riak, Cassandra, and Voldemort are open source datastores with leaderless replication models inspired by Dynamo, so this kind of 
database is also known as Dynamo-style

## Writing to the Database When a Node Is Down
* Send multiple write requests
* Send multiple read requests

### Read repair and anti-entropy
After an unavailable node comes back how does it cope up with
the writes that it missed?

Two mechanisms
#### 1. Read Repair
As we have multiple read requests, Identify and fix nodes that have
stale entries

#### 2. Anti-entropy process
Have a background process to check the consistencies between nodes
and fix them

### Quorums for reading and writing
* Every write must be confirmed by w nodes to be considered successful, 
* and we must query at least r nodes for each read. 
* (In our example, n = 3, w = 2, r = 2.) 
* As long as w + r > n, we expect to get an up-to-date value when reading
* Reads and writes that obey these r and w values are called quorum reads and writes


The quorum condition, w + r > n, allows the system to tolerate unavailable nodes as follows:

* If w < n, we can still process writes if a node is unavailable.
* If r < n, we can still process reads if a node is unavailable.
* With n = 3, w = 2, r = 2 we can tolerate one unavailable node.
* With n = 5, w = 3, r = 3 we can tolerate two unavailable nodes. This case is illustrated in

#### Limitations of Quorum Consistency

1. Monitoring staleness


### Sloppy Quorums and Hinted Handoff
