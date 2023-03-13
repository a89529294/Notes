- `const obj:{} = 1;` is valid; the type `{}` simply refers to any *non null*, *non undefined* value.
- *type predicates* and *assertion functions* are closely related

## void type
- `void` means that the function eventually terminates and returns. It's just that it doesn't return any value. The function either has no `return` statement, or it has a bare `return` statement with no value after it. The `void` type isn't assignable to anything because it represents the absence of a value.

## never type
- A `never` means "this can never actually have a value at runtime."
- Impossible intersections give us the type `never`. Second, `never` can be removed from any union.
- `never` means that the function never terminates normally. It might throw an exception or go into an infinite loop. If we're in a server-side system like Node, it might call `process.exit()` to terminate the process. One way or another, execution never reaches the end of the function. The `never` type is assignable to anything because the compiler knows that the assignment will never actually happen at runtime.

## any type
- The opposite of `never`, `any` means a variable with this type can hold any value at run time.
- Basically disables TypeScript for a variable of type `any`.

## unkown type
- We can assign any value to an `unknown`, just like `any`.
- Unlike `any` TypeScript forces us to check what an `unknown` variable holds before we can do anything with it.

Finally, a note on terminology. `any` means "a variable of any type, assignable to anything". The name `any` is very appropriate; it applies to both reading and writing. `unknown` means "we don't know what's in this variable, so we can't use it until we find out".

