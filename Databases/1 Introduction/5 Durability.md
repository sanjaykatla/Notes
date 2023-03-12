# Durability

> The process of persisting the writes of the transaction or the client that make
> to the database to a non-volatile storage system.

* Changes made by the committed transactions must be persisted in a durable 
non-volatile storage.
* Durability techniques
  * WAL - Write-ahead log
    * Committing will time
  * Asynchronous snapshot
  * AOF - Append only file

## Write ahead log (WAL)
* Writing a lot of data to disk is expensive
  * Indexes
  * Data files
  * Columns
  * Rows
  * etc...
* That is why DBMSs persists a compressed version of the changes known
as WAL

## OS Cache
* A write request in OS usually goes through the OS cache
* When the write go to the OS cache, an OS crash, machine restart
could lead to loss of data.
* Fsync OS command forces writes to always go to disk