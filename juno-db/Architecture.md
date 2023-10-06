# Architecture

JunoDB is distributed KV store designed, built, and open sourced by paypal.

## Storage Servers
JunoDB stores the data on storage servers
These servers accept the operations and makes changes to data.

They can store the data in-memory or on disk

JunoDB is not a pure in memory db.
Data is split into shards (also called partitions). And each storage server is responsible
for bunch of them.

