## Covariance
- Type `T` is *covariant* if given `s <: p` then `T<s> <: T<p>`
- In other words, the sybtyping direction is maintained.
- `Promise<U>` is *convariant*

## Contravaraince
- Type `T` is *contravariant* if given `s <: p` then `T<p> <: T<s>`
- The subtyping direction is reversed.
- Function is *contravariant* when it comes to *paramter types*.

### Function subtyping
- There are two parts to a function type, *parameter* type and *return* type.
- Functions are *covariant* in regards to its *return* type.
- Functions are *contravariant* in regards to its *parameter* type.
- In order for `function A` to be a subtype of `function B` its parameter type must be a supertype of `function B` and its return type must be a subtype of `function B`.

#### Conclusion
- For *higher order functions*, map, reduce, etc, the callbacks they receive can also be a subtype of those callbacks.