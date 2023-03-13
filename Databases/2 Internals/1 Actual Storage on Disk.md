# How indexes and tables are stored on Disk

### Storage Concepts
* Table
* Row ID
* Page
* IO
* Heap Data Structure
* Index Data Structure
* Example of a query

### Row ID
* Internal and system maintained
* In certain databases (mysql - InnoDB) it is same as primary key but other
DBs Postgres have system column row_id(tuple_id)

### Page
* Depending on the storage mode(row vs column), the rows are stored
and read in logical pages
* The DB doesn't read a row, it reads a page or more in a single
IO and we get a lot of rows in that IO
* Each page has a size (8KB postgres, 16KB in mysql)

### IO
* IO operation is read / write request to the disk
* We try to minimize as much as possible
* An IO can fetch one or more depedending on the disk partitions and 
other factors
* An IO can't read a single row
* We want to minimize as much as possible as they are expensive
* Some IO operations goes through the CPU cache not to the disk

### Heap
* Heap is the data structure where every the table is stored and all its 
pages one after another
* This is the actual data where everything is stored
* Traversing the heap is expensive as we need to read so many data
to find what we want
* That is why we need indexes that help us tell where exactly what
part of data is stored. What pages of heap we need to pull

### Index
* An Index is a another data structure separate from heap which has
pointers to the heap
* It has part of data and used to quickly search for something
* You can index on one or more column
* Once you find the value of the index, you can go to the heap to fetch
more information where everything else is there
* Index tells you exactly which page to fetch in the heap
* The index also stored as pages and cost IO to pull the entries of the index
* The smaller the index, the more it can fit in memory and faster the search
* Popular data structure for index is b-trees