# Relational Model vs Document Model

* The best known data model as of today is probably that of sql,
based on relational model proposed by Edgar Codd in 1970. Data is organized into
relations called tables, where each relation is unordered collection of tuples.
* Each competitor to the relational mode generated hype in its time, but it 
never lasted.
  * In 1970 and 1980 network and hierarchical were the main alternatives
  * Object databases come and went again in late 1980s
  * XML databases appeared in 2000s.

## The Birth of NOSQL
* Now, in 2010s, NoSql is the latest attempt to throw the relational
model's dominance
* "NoSQL" is catchy twitter hashtag for a meetup open source,
distributed, non-relational databases in 2009.


The driving forces to NoSQL databases
* A need for greater scalability
* A widespread preference for open source and free databases over
commercial dbs
* Specialized query operations
* Frustration of restrictive relational schema, and desire
for a expressive and dynamic data model

## The Object - Relational Mismatch
* Most of the application are developed using object oriented
programming language.
* Data is stored in relational models, an translator is required between 
the objects in the application code and the data stored in tables.
The disconnect between model is called impendance mismatch.
* **Object-Relational Mapping** like ActiveRecord and Hibernate 
reduces the boilerplate code required for this translation layer, 
they can't completely hide the difference between them.
* Document oriented DBs MongoDB, RethinkDB, CouchDB, and Expresso
supports JSON data model
* The JSON has better locality than multi table schema

## Many-to-One and Many-to-Many Relationships

## Are Document Database repeating history?
* The most popular database for business data processing in 1970s,
was IBM's Information Management System(IMS), Originally developed
for stock keeping in Apollo Space Ship program. 
* Which follows hierarchical model
* IMS worked well for one-to-many relationships.
* But it made many-to-many relations complex
* And it doesn't support joins
* Various solutions were proposed to solve the limitations.
  * Relational Model
  * Network Model
### Network Model
* The network model was standardized by a committee called
Conference for Data Systems Language (CODASYL)
* Also known as CODASYL model
* In the tree structure of hierarchical model
  * Every record has exactly one parent
* In the network model
  * A record could have multiple parents
  * The links between records are not foreign keys
  * But more like a pointers in programming language

### Comparison to document databases
* Document Databases reverted back to the hierarchical model
in on aspect: Storing nested records, (one-to-many relationships
like positions, educations, contact_info) in within their parent
record rather than other table.
* However, when it comes to representing many-to-one and 
many-to-many relationships, relational and document databases are 
not fundamentally different: in both cases, the related item is 
referenced by a unique identifier, which is called a foreign key
in the relational model and a document reference in the 
document model [9]. That identifier is resolved at read time by using a
join or follow-up queries. To date, document databases have not 
followed the path of CODASYL.

## Relational Versus Document Databases Today
* The main arguement in favour of DocM is its schema flexibility
* Better performance due to locality

### Which data model leads to simpler application code?
* If the data in your application has a document like structure, then its good idea
to use DM.
*  if your application does use many-to-many relationships, the document 
model becomes less appealing

### Schema flexibility in the document model
