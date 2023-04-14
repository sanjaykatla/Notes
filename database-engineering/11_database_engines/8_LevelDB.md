# LevelDB

* Written by Jeff and Sanjay from Google in 2011
* Log Structured Merge Tree (LSM) great for high inserts and SSD
* No transactions
* Inspired by BigTable
* Levels of files
  * Memtable
  * Level 0
  * Level 1 - 6
* As files grow large levels are merged
* Used in bitcoin core blockchain, Autocad, Minecraft
