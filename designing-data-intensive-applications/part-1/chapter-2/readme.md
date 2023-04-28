# Chapter 2: Data Models and Query Languages

    Compares several data models and query languages

Data Models are perhaps the most important part of developing software, 
because they have such profound effect: *not only on how we write
the software but also how we think about the proble*m.

Most Applications are build on top of another data model.
For each layer, the key question is how it is going to represented
in the next level.

For example:
1. As application developer, you look at the real world,
and model it in terms of data structures, APIs that manipulate
that data structure, Those structure are often specific to your
application.
2. When you want to store these data structures who express them
in terms of general purpose data, such as JSON, XML documents,
tables in relational db, of graph model.
3. The engineer who built database software decided on a way
of representing the JSON/XML/TABLE/Graph in terms of bytes in 
memory, on disk, or on network.
4. On yet lower levels, hardware engineers have figured out how
to represent bytes in terms of electrical currents, pulses of light,
magnetic fields and more.
5. 

### Relational Model vs Document Model
* The Birth of NOSQL
* The Object - Relational Mismatch
* Many-to-One and Many-to-Many Relationships
* Are Document Databases repeating history?
* Relation DB vs Document DB Today
### Query languages for Data
### Graph like Data Models