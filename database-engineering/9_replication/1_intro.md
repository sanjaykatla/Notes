# Database Replication

> Sharing info to ensure consistency, fault tolerance.

### Agenda
* Master backup vs multi master Replication
* Synchronous vs Asynchronous Replication
* Demo with Postgres
* Pros and Cons
* Summary


## Master / Backup (Standby) Replication
* One master / leader node accepts the writes / ddls
* One or more backup / standby nodes that receive those writes
from the master
* Simple to implement no conflicts

## Multi Master Replication
* Multiple master / leader nodes that accepts writes / ddls
* One or more backup or follower nodes that receive those writes from
masters
* Need to resolve conflicts

## Synchronous vs Asynchronous Replication
> A write transaction to the master will  be blocked until
it is written to the backup / standby nodes

>A write transaction is considered successful if it written
> to the master, then asynchronously the writes are applied
> to backup nodes


### Pros and Cons

#### Pros
* Horizontal Scaling
* Region based queries 

#### Cons
* Eventual consistency
* Slow writes
* Complex to implement
* 