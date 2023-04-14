# Hash Table

### Two ideas to construct Hash Table
1. Application key to hash key [0,n]
   * apple -> 12567432
2. Hash key to a smaller range[0,m]
   * 12567432 -> 17

### Conflict resolution technics
1. Chaining
   * Use auxiliary space to store
2. Open addressing
   * Use empty slots instead of auxiliary space.
   * Linear Probing
     * Fast
     * Locality of Reference
     * Clusters of collision
   * Quadratic Probing
   * Double Hashing

### Resizing
1. Re-insert all keys
2. Just adjust the pointers