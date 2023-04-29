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
* 