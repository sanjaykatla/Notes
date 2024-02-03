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
10. 