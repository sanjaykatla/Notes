# SQL vs NoSQL

* Default database option should be sql


Ecommerce website

Products

1. Separate tables for each product
   2. Too many tables
   3. Show top selling products -> need to join many tables
2. Products tables with attributes in JSON
   3. Joins
   4. Queries
   5. Constraints
   6. Using no sql tech to backported sql

## Sharding in RDBMS
1. Nullifies the ACID properties
2. Sharding key should be chosen carefully
3. Frequent / important queries should go to one shard only
4. Amount of possible shards is high
   5. User_id, user_age, gender
5. Data should be distributed evenly

### Example sharding key
1. Vehicle rental / riding app
   2. sharding key will be city
3. Train tatkal system
   4. sharding key will be train number
5. Messaging app, personal chat, group chat
   6. optimize for reads
   7. sharding key will be user_id
8. Slack
   9. Group_id

* SQL is bad for analytics

## NOSQL

### Key-Value store
1. HashMap
2. Redis - In memory
3. Memcached - In memory
4. DynamoDB - DB

#### methods
1. get
2. set
3. has(key)

### Document store
Unstructured objects
Json Data
1. MongoDB
2. Firebase - DB
3. ElasticSearch
4. CouchDB


### Column store
* Suitable for aggregations query

1. Cassandra
2. BigTable
3. HBase
4. ScyllaDB

### Graph store

1. Neo4j
2. SurrealDB
3. AWS GraphDB
4. Prometheus

### File/Blob store
1. AWS S3
2. HDFS

### Other
1. VectorDB
   2. Nearest neighbour search

