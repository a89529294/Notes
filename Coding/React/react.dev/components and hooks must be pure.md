_Side effects are a broader term than Effects_. Effects specifically refer to code that’s wrapped in `useEffect`, while a side effect is a general term for code that has any observable effect other than its primary result of returning a value to the caller.

Side effects are typically written inside of [event handlers](https://react.dev/learn/responding-to-events) or Effects. But never during render.

_In most cases, you’ll use [event handlers](https://react.dev/learn/responding-to-events) to handle side effects_. Using an event handler explicitly tells React that this code doesn’t need to run during render, keeping render pure. If you’ve exhausted all options – and only as a last resort – you can also handle side effects using `useEffect`.