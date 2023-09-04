1. Only use the global `Router` object outside of the React lifecycles (i.e. inside `useEffect` or event handlers)
2. Use `useRouter` in function components, or `withRouter` for Class components
    
In general, the difference is that the global `Router` object always points to the latest global state at _any given time_, whereas `useRouter`/`withRouter` refer to _the route being rendered_.

An easier way to think about it might be that `useRouter`/`withRouter` are actually `route`s that happen to also include router functions (like `push`), where the global `Router` object is a bundle of router functions (like `push`) that happens to also include the latest state for the current `route`.