# Write-ahead logging (WAL)

* For any database system, reliability is super important
* It does everything to ensure reliability

### Upon a transaction is committed.

1. Data is written to a non-volatile storage
2. Index will be updated
   1. Could be non volatile storage again
3. Disk writes are complicated

>    RAM --> OS Cache --> Disk Cache --> Disk

### Write ahead log
Standard method for ensuring Data Integrity
> Core idea is before making changes to actual datafile, 
> log these changes describing the changes.

* Keep the file open in sync mode
* Just dump all the queries as first thing as part of the transaction
* No need log the select queries

### Advantages:
* We do not need to flush the data changes on every commit
* In case of disaster, we can reply the logs 
* Refuces the number of disk writes
* Point-in-time is recovery is possible.
* 
