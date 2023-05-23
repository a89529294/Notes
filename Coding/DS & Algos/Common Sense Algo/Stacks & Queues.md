They are simply *arrays with restrictions*.

More specifically, **stacks and queues** are elegant tools for handling *temporary data*.

Think of *temporary data* like the *food orders in a diner*. What each customer orders is important until the meal is made and delivered; then you throw the order slip away.

*Temporary data* is information that doesn’t have any meaning after it’s processed, so *you don’t need to keep it around*.

## Stack
*LIFO*: last in first out
A **stack** stores data in the same way that arrays do—it’s simply a list of elements. The one catch is that stacks have the following three constraints:
1. Data can only be inserted at the end.
2. Data can only be read from the end.
3. Data can only be removed from the end.


## Queue
_FIFO_: first in first out
A **queue** also deals with temporary data elegantly, and is like a stack in that it is an array with restrictions.
Like stacks, queues are arrays with three restrictions:
1. Data can only be inserted at the end.
2. Data can only be read from the front of a queue.
3. Data can only be removed from the front of a queue.
