# Row Based vs Column Based Storage

## Row Based
* Tables are stored as rows on disk
* A single IO read to the table fetches multiple rows will all their column
* More Ios are required to find particular row in a table scan, but once you 
find out you will get all column values