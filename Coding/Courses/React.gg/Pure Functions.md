A **function** as a process which takes some input, an argument, and calculates some output, a return value.

A **pure function** is one that given the same input, always return the same output and does nothing else.

Any time a function does **anything** other than this, whether through *relying on state other than the input value* it receives or *creating an observable change to the program* itself, it's said to have a side effect.

## Pure Functions in React
A _component_ is pure if the only thing it does is take in _state_ and _props_ and return _jsx_.  Anything else, fetching, using browser api, etc, count as side effects.



