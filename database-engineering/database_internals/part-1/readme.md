# Storage Engines

```
Primary job of a DBMS is reliably store the data and making it
available for users.
```

### Parts of an DBMS
1. A transport layer
   * Accepting requests
2. A query processor
   * Determining the most effective way to run queries
3. An execution engine
   * Carrying out the operations
4. Storage engine
   * Software component responsible for storing, retrieving and managing memory
in memory and disk.

> The DBMSs are built on top of storage engines offering
> a schema, a query language, indexing, transactions, and many other useful 
> features.
> 

### Sample Database Engines
1. BerkeleyDB
2. LevelDB
3. RocksDB
4. LMDB
5. Libmdbx
6. Sophia
7. HaloDB

### DBMS Architecture
### Memory-versus-Disk based DBMS
### Column-versus-Row oriented DBMS
### Data files and index files
### Buffering, Immutability, and Ordering

