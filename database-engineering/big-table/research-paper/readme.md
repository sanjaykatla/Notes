# Bigtable: Distributed Storage System for Structured Data

Big table is distributed storage system for managing structured
data. It is designed to scale to a very large size: petabytes
of data.

```
Section 1: Introduction
Section 2: Data Model
Section 3: API
Section 4: Building Blocks
Section 5: Implementation
Section 6: Refinements
Section 7: Performance Evaluation
Section 8: Real Applications
Section 9: Lessions
Section 10: Related Work
Section 11: Conclusions
```

## Section 1: Introduction
* Bigtable is designed to relaible scale to petabytes of data on thousands of machines
* Bigtable has achieved wide applicability, scalability, high performance
and high availability.
* It shares many implementation strategies with databases. Parallel Databases, In-memory
databases
* It doesn't support full relational model.

## Section 2: Data Model
* Bigtable is a sparse, distributed, persistent multi-dimensional sorted map
* The map is indexed by a row key, column key, and timestamp; 
  * each value in the map is an uninterpreted array of bytes.
* 