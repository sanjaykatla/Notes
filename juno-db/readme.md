# JunoDB

## Language

1. It started as single threaded C++ program
2. But got rewritten in golang
    1. Highly concurrent - goroutines
    2. Multi-core functionality
3. JunoDB is well suited for CPU heavy workloads

## Common Use cases

### 1. Caching
JunoDB is often used as a temporary cache
    2. TTL from few seconds to few days
1. User Token
2. Account Details
3. API responses
4. User preferences

### 2. Idempotency
Avoids duplicate processing
retries are painful.

### 3. Latency Bridging
Juno DB has really fast inter cluter replication
