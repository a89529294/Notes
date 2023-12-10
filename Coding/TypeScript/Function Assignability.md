### Function sub typing
- There are two parts to a function type, *parameter* type and *return* type.
- To check if `x` is assignable to `y`, we first look at the parameter list. Each parameter in `y` must be assignable to corresponding parameter in `x`. Note it is ok for `x` to have fewer parameters in `y`.
- Next look at the return types. The return type of `x` must be assignable to the return type of `y`.
- This is how callback functions for `map`,`reduce`, etc works, we generally pass in fewer arguments then specified. 

#### Conclusion
- For *higher order functions*, map, reduce, etc, the callbacks they receive can also be a subtype of those callbacks.