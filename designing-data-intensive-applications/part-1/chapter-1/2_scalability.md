# Scalability

Scalability is an ability of a system to grow and server the
increased load.

## Describing the Load
* No of requests per second to a web server
* The ratio of reads to writes in a database
* The number of simultaneously active users in a chat room
* The hitrate on the cache

## Describing the Performance

* Once you have described the load on your system, we can investigate
what happens when the load increases
  * When you increase load parameter and keep the system resources
    (CPU, Memory, NWB, etc..) unchanges, how is your performance effected.
  * When you increase load parameter, how much do you need to 
  increase the resources to keep the performance unchanged.

### Performance
* In a batch system like Hadoop, we usually care about throughput - of number
of records inserted per sec.
* In online systems, usually response time is more important

#### Latency vs Response time
> Response time is usually what user sees: besides what is the actual
> time taken to process

> Latency is duration that a request is waiting to be handled.

Average / Mean:
* Doesn't tell you how many users seen that delay.

Median / 50 % / p50 : 
* Is also known as 50th percentile.
* Half of the users seen less than median delay, and other half
more than median delay
* Median refers to the single request.

    
    p50, p95, p99, p999

## Approaches for Coping with Load
* Vertical Scaling
* Horizontal Scaling
