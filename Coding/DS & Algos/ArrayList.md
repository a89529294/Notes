An array that is allowed to grow.

When implementing an *arrayList* we simply use an array as the underlying data structure while keepign an eye on the length. Once we are about to exceed the length simple create a bigger array and copy the elements to the new array.

*head* is always at index 0
*tail* is always the latest added element

## Pros 
1. *constant* time access
2. *constant* time push & pop

## Cons
1. *linear* time shift & unshift, since we need to move all the elements.
