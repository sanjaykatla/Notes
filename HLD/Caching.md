# Caching

Scale is large
1. Read Heavy
2. Write Heavy

Caching helps us handle a large read heavy.


## Cache eviction policies
* LRU
* LFU
* FIFO
  * Example: Watching a video, then segments are evicted in FIFO order
* LIFO
## Cache invalidation strategies
* Time to live
  * out dated data will be deleted for every request
  * Fast reads
  * Fast writes
* Write through
  * Immediate consistency
  * Insert into cache
  * Insert into DB
  * App server becomes complex
    * Need to write only when DB write is successful
    * Ow rollback cache write
    * 2PC protocol
  * Slow writes
* Write back
  * Just write to cache and save to db later
* Write around (similar to TTL)
    * Eventual consistency
    * Cron job runs every 2 hours and updates the cache
    * Fast reads
    * Fast writes
* Write behind

### Speed of the SSD and HDD:
SSD - best 3 GBPS, avg - 2 GBPS
HDD - 300 MBPS