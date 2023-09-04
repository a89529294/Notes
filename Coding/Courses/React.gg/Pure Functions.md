A **function** as a process which takes some input, an argument, and calculates some output, a return value.

A **pure function** is one that given the same input, always return the same output and does nothing else.

Any time a function does **anything** other than this, whether through *relying on state other than the input value* it receives or *creating an observable change to the program* itself, it's said to have a side effect.

More specifically, a _pure function_ satisfies the following:
1. Return the same result given the same arguments.
2. Do not change the external state of the program.
3. Do not perform any [I/O operations](https://en.wikipedia.org/wiki/Input/output) (like reading from disk, accessing the internet, or reading from the console)
4. Rely on state other than arguments
5. Do not call any functions that do any of the above

## Pure Functions in React
A _component_ is pure if the only thing it does is take in _state_ and _props_ and return _jsx_.  Anything else, fetching, using browser api, etc, count as side effects.

## I/O Operations
When we say "i/o" (which stands for input/output) as developers, we're usually talking about the parts of our program that interact with the outside world. _Outside world_ just means anything that's not in-memory of our running program.



