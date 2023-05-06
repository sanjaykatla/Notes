# Problems with Replication Lag

## Reading Your Own Writes
* If user has modified or updated something recently, read from
master

## Monotonic Reads
* One way of achieving monotonic reads is to make sure that each user always makes their reads from the same replica
(different users can read from different replicas)

## Consistent Prefix Reads
Preventing this kind of anomaly requires another type of guarantee: consistent prefix reads [23]. This guarantee says that if a sequence of writes happens in a certain order, then anyone reading
those writes will see them appear in the same order.

