# Introduction and Overview

Database Systems can serve different purposes
1. Some are used primarily for hot data
2. Some serve as long-lived cold storage
3. Some allow complex analytical query
4. Some allow accessing data by values
5. Some are optimized to store time series data
6. Some store large blobs


1. Transport Layer
   1. Cluster Communication
   2. Client Comminication
2. Query Processor
   1. Query Parser
   2. Query Optimizer
3. Execution Engine
   1. Remote Execution
   2. Local Execution
4. Storage Engine
   1. Transaction Manager
   2. Lock Manager
   3. Access Methods
   4. Buffer Manager
   5. Recovery manager

## Memory- Versus Disk-Based DBMS
Main memory database systems are different from 
their disk-based counterparts not only in terms 
of a primary storage medium, but also in which 
data structures, organization, and optimization 
techniques they use.

