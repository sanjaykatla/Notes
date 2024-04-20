# Cassandra

1. Wide column database
2. Completely distributed and can scale to huge number of nodes across multiple data centers
3. It has out of the box support for replication / distribution
4. It has decentralized architecture, where there is no single point of failure
5. Having primary / coordinator nodes can become a bottleneck
when scaling the system, cassandra solves this problem by having
the every node in the cluster be the same.
6. Any node can accept read / write requests, and can communicate
using a gossip protocol in a peer-to-peer way.
7. Cassandra is optimized for write heavy operations
8. Cassandra uses Log Structured Merge Trees (LSM Trees) for storage
9. 