Put simply, **rendering** is just a fancy way of saying that React *calls your component* with the intent of eventually updating the View.

React will **only re-render** when the *state of a component changes*.

React will **only re-render** if the event handler contains an invocation of `useState`'s updater function **and** React sees that the new state is different than the state in the snapshot

Whenever React encounters multiple invocations of the same updater function (e.g. `setCount` in our example), it will keep track of each of them, but *only the result of the last invocation will be used as the new state*. 
But there is a way to *tell React to use the value of the previous invocation* of the updater function instead of replacing it.
```js
const handleClick = () => {
  setCount(1)
  setCount(2)
  setCount(3) /* the new count will be 3 */
}

const handleClick = () => {
  setCount(1)
  setCount(2)
  setCount((c) => c + 3) /* the new count will be 5 */
}

const handleClick = () => {
  setCount(1)
  setCount((c) => c + 3)
  setCount(7)
  setCount((c) => c + 10) /* the new count will be 17 */
}
```

React will only re-render **once** per event handler, even if that event handler contains updates for multiple pieces of state.




