# Partitioning

### Agenda
* What is partitioning
* Horizontal vs Vertical
* Partitioning types
* Partitioning vs Sharding
* Demo
* Pros and Cons


## Partitioning
* **Horizontal Partitioning**: Way of splitting the rows into multiple tables called partitions
  * Range or list
* **Vertical Partitioning**: Way of splitting the columns into multiple partitions
  * Large Column (blob) that you can store in a slow access drive in its tablespace


### Partition Types
#### By Range
* Dates, ids
#### By List
* Discrete values or zip codes
#### By Hash
* Hash Functions (Consistent Hashing)

## Horizontal Partitioning vs Sharding 
* HP splits big table into multiple tables in the same database, client is agnostic
* Sharding splits big table into multiple tables across multiple database servers.
* HP table name changes (or changes)
* Sharding everything is same but database server changes