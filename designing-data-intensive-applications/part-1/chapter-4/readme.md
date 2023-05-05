# Chapter 4. Encoding and Evolution


When a data format or schema changes, a corresponding change to application code often needs to happen

* This means that old and new versions of the code, and old and new 
data formats, may potentially all coexist in the system at the same time. 
* In order for the system to continue running smoothly, we need to maintain compatibility in both directions:

### Backward compatibility
Newer code can read data that was written by older code.

### Forward compatibility
Older code can read data that was written by newer code.

## Formats for Encoding Data
Programs usually work with data in (at least) two different representations:
1. In Memory
2. When you want to write data to a file or send it over the network

### Language-Specific Formats
Many programming languages come with built-in support for encoding in-memory objects into byte sequences


## Binary encoding


### Thrift and Protocol Buffers

* Protobuf - Developed at Google
* Thrift - Developed at Facebook
  * Thrift has two different binary encoding formats,iii called
  BinaryProtocol and CompactProtocol, respectively
* Both Thrift and Protocol Buffers require a schema for any data that is encoded.