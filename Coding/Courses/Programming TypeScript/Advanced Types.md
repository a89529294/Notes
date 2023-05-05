## subtype & supertype
If you have two types `A` and `B`, and `B` is a *subtype* of `A`, then you can safely use a `B` anywhere an `A` is required.

## subtyping functions
A function A is a *subtype* of function B if A has the *same or lower arity* (number of parameters) than B and:

1. A’s this type either isn’t specified, or is >: B’s this type.
2. Each of A’s parameters is >: its corresponding parameter in B.
3. A’s return type is <: B’s return type.
 
## assignability
For _non-enum types_—like arrays, booleans, numbers, objects, functions, classes, class instances, and strings, including literal types—`A` is assignable to `B` if either of the following is true:
1. A is a *subtype* of B
2. A is `any` 

## type widening
In general, TypeScript will be *lenient when inferring your types*, and will err on the side of inferring a more general type.

