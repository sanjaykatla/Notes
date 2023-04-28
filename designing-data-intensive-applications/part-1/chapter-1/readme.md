# Chapter 1. Reliable, Scalable, and Maintainable Applications

* Many applications are data intensive
* A data intensive application is typically built from standard building blocks
the provide commonly needed functionality.
* Example, most of the applications need to:
  * Store data so that they, or another application can find it later - 
    **(databases)**
  * Remember the result of an expensive operation, to speed up reads - **caches**
  * Allow users to search data by keyword or filter it in varioud ways (search indexes)
  * Send a message to another process, to be handled asynchronously (stream processing)
  * Periodically crunch the data accumulated  (batch processing)

## Thinking about data systems

We typically think about databases, queue, caches, etc. as being very different
categories of tools.

Although a database and a message queue have some superficial similarity - both store
data for some time - they have very different access pattern, which means different
performance characteristic, hence different implementation.

* There are databases used as message queues - Redis
* There are message queues with durability guarantee - Kafka

In this chapter we focus on
1. Reliability
2. Scalability
3. Maintainability