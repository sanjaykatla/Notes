# Database Engines

* Sometimes called database engines, storage engines, embedded database, or
software libraries that DBMS uses to do low level storing of data on disk.

### Agenda
* What is database engine?
* MyISAM
* Aria
* InnoDB
* XtraDB
* LevelDB
* RocksDB
* SQLite
* Berkeley DB
* Demo
### What is database engine?
* Library that takes care of the on disk storage and CRUD
  * Can be as simple as key-value store
  * Or as rich and complex as full support ACID with transactions with foreign key
* DBMS can use Database engine and build feature on top of it.
  * Server
  * Replication
  * Isolation
  * Stored Procedures
* Want to write a database? Don't start from scratch use database engine.
* Sometimes referred as storage engine, embedded databse.
* Some DBMS gives you flexibility to choose the engine like MySql and MariaDB
* 