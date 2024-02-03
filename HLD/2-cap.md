# CAP

What we can do, what we can't do

### 1. No Consistency
* Write - 1 master
* Read - any 1 slave

* Stale Data - sync issue
* Data loss -  in case master db crashes
* High Availability


#### Performance:
* Read - fast
* Write - fast

### 2. Eventual Consistency
* Write - 1 master and 1 slave(2 places)
  * 2 phase commit
* Read - any 1 slave

* Stale data - sync issue
* No Data loss
* High Availability

#### Performance:
* Read - fast
* Write - slow (2 places, commit, rollback)

### 3. Strong Consistency

* Write - 1 master and all slave(2 places)
    * 2 phase commit
* Read - any 1 slave

* No Stale data
* No Data loss
* Partial Availability
  * Reads - High Availability
  * Writes - No Availability

#### Performance:
* Read - fast
* Write - very slow (2 places, commit, rollback)
  * Fan-out write

### 4. Immediate Consistency via Quorum:
* Write - at least (n+1)/2 servers
    * 2 phase commit
* Read - at least (n+1)/2 servers

* No Stale data
* No Data loss
* Partial Availability
    * Reads - High Availability
    * Writes - No Availability

#### Performance:
* Read - slow
* Write - slow (2 places, commit, rollback)

### 5. Tunable Consistency
Example: Cassandra