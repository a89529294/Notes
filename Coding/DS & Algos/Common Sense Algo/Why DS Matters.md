- When we measure how *“fast”* an operation takes, we do not refer to how fast the operation takes in terms of pure time, but instead in *how many steps it takes*.
- Measuring the *speed of an operation* is also known as measuring its *time complexity*. Throughout this book, we’ll use the terms *speed*, *time complexity*, *efficiency*, and _performance_ interchangeably.

## array operations
### read
- When a program declares an array, it allocates a contiguous set of empty cells for use in the program.
- Every cell in a computer’s memory has a specific address. It’s sort of like a street address (for example, 123 Main St.), except that it’s represented with a simple number. Each cell’s memory address is one number greater than the previous cell.
- Recorded in each array is the memory address which it begins at. So the computer has this starting address readily.
- A computer can jump to any memory address in one step.
- *Takes one step to read*.
### search
- For N cells in an array, *linear search takes a maximum of N steps*.
### insert
- In a worst-case scenario can take up to *N + 1 steps* for an array containing N elements. This is because the worst-case scenario is inserting a value into the beginning of the array in which there are N shifts (every data element of the array) and one insertion.
### delete
- the maximum number of steps that deletion would take is *N steps*.

## array-based set operations
### insert
- insertion into a set in a *best-case scenario, i.e. at the end of the set, will take N + 1 steps* for N elements. This is because there are N steps of search to ensure that the value doesn’t already exist within the set, and then one step for the actual insertion.
- In a *worst-case scenario, where we’re inserting a value at the beginning of a set*, the computer needs to search N cells to ensure that the set doesn’t already contain that value, and then another N steps to shift all the data to the right, and another final step to insert the new value. That’s a total of *2N + 1 steps*.
### read, search, delete
- are the same as arrays
