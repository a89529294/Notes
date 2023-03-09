- `const obj:{} = 1;` is valid; the type `{}` simply refers to any *non null*, *non undefined* value.
- *type predicates* and *assertion functions* are closely related

## never type
- A `never` means "this can never actually have a value at runtime."
- Impossible intersections give us the type `never`. Second, `never` can be removed from any union.

## any type
- The opposite of `never`, `any` means a variable with this type can hold any value at run time.
- Basically disables TypeScript for a variable of type `any`.

## unkown type
- We can assign any value to an `unknown`, just like `any`.
- Unlike `any` TypeScript forces us to check what an `unknown` variable holds before we can do anything with it.

Finally, a note on terminology. `any` means "a variable of any type, assignable to anything". The name `any` is very appropriate; it applies to both reading and writing. `unknown` means "we don't know what's in this variable, so we can't use it until we find out".

