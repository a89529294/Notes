A **linked list** is a data structure that represents a list of items, just like an array.
The difference is cells in an array are contiguous, while they are not in a linked list.
In addition to the data stored within the node, each node also stores the memory address of the next node in the linked list.

## linked list v.s. array
| operation | linked list | array |
| --------- | ----------- | ----- |
| read | O(N) | O(1) |
| search | O(N) | O(N) |
| insert | O(N) (O(1) at start) | O(N) (O(1) at end)|
|delete | O(N) (O(1) at start) | O(N) (O(1) at end)|

## doubly linked list
A **doubly linked list** is like a linked list, except that each node has two links— one that points to the next node, and one that points to the preceding node. In addition, the doubly linked list keeps track of both the first and last nodes.

The biggest upside is *inserting and deleting at start and beggining are both O(1)*!

