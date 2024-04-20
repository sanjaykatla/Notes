# Transactions

#### The slippery of a Tranaction
#### Weak Isolation Levels
#### Serializability


### What are the thing can go wrong?
1. hardware or software may go down
2. Network my go down
3. Partial writes may be successful
4. Writing data at the same time
5. Race conditions
6. Overwrites

## Isolation

### Read Committed

The most basic level of transaction isolation is read committed.v It makes two guarantees:

* When reading from the database, you will only see data that has been committed (no dirty reads). 
* When writing to the database, you will only overwrite data that has been committed (no dirty writes).
* The most basic level isolation level

#### No Dirty Reads
There are a few reasons why it’s useful to prevent dirty reads:
* If a transaction needs to update several objects, a dirty read means that another
transaction may see some of the updates but not others
* If a transaction aborts, any writes it has made need to be rolled back

#### No Dirty Writes


