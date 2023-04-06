# gRPC Load Balancing

## Channel
* Channel is an abstract over a connection it represents the connection between client and server.
* The connection is persistent
* This uses HTTP2 protocol
* Default time is 30m but configuration
* Connection creation is Lazy, and established during first rpc.
* Thread safe
* Single open connection can be used for multiple requests

### Load Balancing types
* Server side LB
* Client side LB