See implementation in my kata-machine directory

There are two parts to this
1. `LinkedList` itself, some of the potential properties and helper methods
	1. `head`
	2. `tail`
	3. `size`
	4. `get(idx:number):T`
	5. `insertAt(idx:number,val:T):void`
	6. `deleteAt(idx:number):void`
	7. ... and more
1. `LinkedNode` which can be *singly* linked, or *doubly* linked
	1. `val` value of the node, can be anything
	2. `next: LinkedNode | undefined` for both doubly and singly linked nodes
	3. `prev: LinkedNode | undefined` only for doubly linked nodes