When we calculate the dimensions of elements inside the _useEffect_ hook and then hide them or adjust their size, we might see the visual "glitch".
This is happening because normally _useEffect is run asynchronously_. _Asynchronous code is a separate task from the browser's perspective. So it has a chance to paint the state "before" and "after" the change_, resulting in the glitch.

We can prevent this behavior with the _useLayoutEffect_ hook. This hook is run _synchronously_. From the browser's perspective, it will be one large, unbreakable task. So the _browser will wait and will not paint anything until the task is complete and the final dimensions are calculated_.

Note if there is a _setState_ in _useLayoutEffect_, if will get run synchronously, i.e.
`render`->`useLayoutEffect`->`state changes`->`re-render`->`browser paint`.


