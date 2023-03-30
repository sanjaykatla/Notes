# GRPC

### Why GRPC?
#### Problems with Micro Services
1. To form a TCP connection with HTTP 1.1 it takes 3 calls to server
2. HTTP is stateless and request carries information in the form of Header
   * This information is plain text and cannot be compressed
3. Serialization & De-serialization
4. No strict contract
5. Client SDK

## Stubby
* RPC Framework from Google
* 15 Years
* 10 billions reqs / sec
* Cross platform
* Tightly coupled with infrastructure


## gRPC
* Developed by Google
* Inspired by Stubby
* Released in 2016
* Adopted by Netflix, MS
* Belongs to CNCF


## gRPC - Benifits
* HTTP2 is default
  * Binary
  * Multuplexing
  * Flow-control
* Non-blocking, Streaming bindings
* Protobuf
  * Strict typing
  * DTO
  * Service notifications
  * Language agnostic
  * Auto-generated bindings for multiple languages
* Great for mobile apps

