# B-Tree
* Balanced data structure for fast traversal.
* B-Tree has nodes
* In B-Tree of m nodes, some nodes can have m child nodes
* Nodes has upto m-1 elements
* Each element has a key and value
* The value usually data pointer to the row
* Data pointer can point to primary key or tuple
* Root node, leaf node, internal node
* A node = disk page


## How B-Tree improve performance
![img.png](images/b_tree_helps.png)

## Limitation of B-Tree

* Elements in each all nodes store both the key and value
* Internal nodes take more space thus require more IO
and can slowdown the traversal
* Range queries are slow because of the random access
* B+ Trees solves these problem