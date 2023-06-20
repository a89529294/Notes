## Rule #0
When a component renders, it should do so without running into any side effects.

## Rule #1
If a side effect is triggered by an event, put that side effect into an event handler.

## Rule #2
If a side effect is synchronizing your component with some external system, put that side effect into useEffect.

## Pure Functions in React
A _component_ is pure if the only thing it does is take in _state_ and _props_ and return _jsx_.  Anything else
- api calls
- manual DOM manipulations
- using browser APIs like localStorage, setTimeout
is a side effect.