An algorithm is a set of instructions for accomplishing a task.
*Binary search* only works for sorted lists.

## Big O
Big O notation lets you compare the number of operations. It tells you how fast the algorithm grows.
It establishes the worst case scenario.
A list of common *Big O* run times, from fastest to slowest
1. O(log n), e.g. binary search
2. O(n), e.g. simple search
3. O(nlog n), e.g. quick sort, remember to choose a random pivot
4. O(n<sup>2</sup>), e.g. selection sort
5. O(n!), e.g. traveling sales person

### Conclusion
- Algorithm speed isn’t measured in seconds, but in growth of the number of operations.
- Instead, we talk about how quickly the run time of an algorithm increases as the size of the input increases.