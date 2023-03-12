# Transaction

## What is Transaction
>A collection of SQL Queries that are treated as one unit of work.

Example:
* An account deposit
  1. Select amount to check sufficient amount
  2. Deduct from sender account
  3. Credit recipient

### Transaction Life Span

#### Transaction BEGIN
> This indicates the database that we are about to start a transaction
> with multiple queries in it.

#### Transaction COMMIT
> This is to ensure the persistence

#### Transaction ROLLBACK
> This is to undo all changes done by the queries

#### Nature of Transactions
* Usually transactions are used to update or change the data.
* However, it is perfectly normal to have a readyonly transaction

![img.png](images/transaction.png)