# GRPC

* High performance open source RPC Framework
* Developed at Google
* Client app directly invokes server method on a different machine
* Service is defined using proto
* More of action oriented instead of resource oriented


## gRPC Synchronous vs Asynchronous

* Clients call to server can be Sync / ASync
* It is completely up to the client
  * It also depends on the RPC

### RPC Types
* Unary 
* Server streaming
* Client Streaming
* Bidirectional Streamingx