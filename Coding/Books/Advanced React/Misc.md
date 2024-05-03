### setState in callbacks, useEffects vs setState during renders
`setState` in `callbacks/useEffects` are asynchronous, i.e. they are batched and causes a pending state transition. 
`setState` in the _render phase_ is _synchronous_, e.g. state changes will be applied immediately after the return statement , and can lead to issues like infinite loops because it can interrupt the current render and start a new one immediately.

### rare example of using setState during render
```jsx
import { useState } from 'react';

export default function CountLabel({ count }) {
  const [prevCount, setPrevCount] = useState(count);
  const [trend, setTrend] = useState(null);
  if (prevCount !== count) {
    setPrevCount(count);
    setTrend(count > prevCount ? 'increasing' : 'decreasing');
  }
  return (
    <>
      <h1>{count}</h1>
      {trend && <p>The count is {trend}</p>}
    </>
  );
}
```
- Note that the 2 `setState`s are still _batched_ in the if block.
- You need to have a check like `prevCount !== count` to prevent infinite loops. 
- this pattern can be hard to understand and is usually best avoided. However, it’s better than updating state in an effect. When you call the `set` function during render, React will re-render that component immediately after your component exits with a `return` statement, and before rendering the children. This way, children don’t need to render twice. The rest of your component function will still execute (and the result will be thrown away). If your condition is below all the Hook calls, you may add an early `return;` to restart rendering earlier.