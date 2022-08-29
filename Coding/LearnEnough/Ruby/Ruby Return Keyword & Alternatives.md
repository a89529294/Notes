# Return & Friends
- `return` terminates the *method* or *lambda* it is in.
- `next` terminates the *block*, *proc*, or *lambda* it is in.
- `break` terminates the *method* that yielded to the block or invoked the proc or lambda it is in.

## What are methods, blocks, lambdas?
- A *block* is not an object and is created by `{ … }` or `do … end`.
- A *proc* is a `Proc` object created by `Proc.new` or `proc`.
- A *lambda* is a `Proc` created by `lambda`.

