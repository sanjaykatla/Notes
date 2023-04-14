# B+ Trees

* Exactly like B Trees but only stores key in the internal nodes
* Values are stored only in leaf nodes
* Internal nodes are smaller since they only store key and can fit in more elments
* Leaf nodes are doubly linked, so once you find the key you can find all values before and after it.
 * Great for range queries
 * ![img.png](images/b+_tree.png)
 
## DBMS Considerations
* Cost of leaf pointer cheap
* One nodes fits a DBMS page
* Can fit internal nodes easily in memory for fast traversal
* Leaf nodes can live in data files in heap
* Most DBMS use B+ trees