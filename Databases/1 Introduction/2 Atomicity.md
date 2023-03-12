# Atomicity

> Atomicity is the idea of the transaction being treated as one unit of 
> work and cannot be split as an property of an atom. 

1. All queries in a transaction must succeed.
2. If one query fails, all the prior successful queries should rollback.
   * Could be duplicate primary key entry
   * Failed constraint
   * Invalid SQL syntax
3. If a database went down prior to a commit of a transaction, all the 
successful queries in the transaction must rollback.
4. An Atomic transaction is a transaction that will rollback all queries if
one or more queries failed.
5. The database should cleanup after restart.
