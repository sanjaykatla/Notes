# LCR algorithm for Leader Election

Leader election is a automated way of system recovery, when the leader node is 
down, the leader election algorithm is triggered which elects the new leader thus 
restoring the system.



Algorithm works when the total number of nodes are unknown.

Assumptions:
* Every node has unique UID
* UIDs are comparable
* Every nodes knows its immediate.
* Clock-wise neighbours

## The Algorithm
Every node participates in the election and pitches itself
to be the new leader.

#### Pitch
Creates a message with its UID and send it to its neighbours.

When a node receives a UID, it compares the incoming with its own UID

> If incoming UID > own UID : forwards UID to its neighbours

> If incoming UID < own UID : discard the incoming UID

> If incoming UID = own UID : declares itself as the leader.

Because every single node participates, the message with the largest
UID will survive and will eventually reach the node from where it started.
The node will thus know it has the largest UID and hence new leader.


The new leader will be announced through the another message passed across the
topology.

The new leader receives this report msg
 - Halts the election process
 - Stores the new leader informaiton locally
 - Forwards the message to the next node.


### Complexity

Since each node pitches itself and the message may make entire trip.
the worst case complexity (#messages) is O(n^2)  n is the number of nodes in the 
topology.

