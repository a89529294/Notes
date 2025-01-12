Strict Mode enables the following development-only behaviors:

- Your components will [re-render an extra time](https://react.dev/reference/react/StrictMode#fixing-bugs-found-by-double-rendering-in-development) to find bugs caused by impure rendering.
- Your components will [re-run Effects an extra time](https://react.dev/reference/react/StrictMode#fixing-bugs-found-by-re-running-effects-in-development) to find bugs caused by missing Effect cleanup.
- Your components will [re-run refs callbacks an extra time](https://react.dev/reference/react/StrictMode#fixing-bugs-found-by-re-running-ref-callbacks-in-development) to find bugs caused by missing ref cleanup.
- Your components will [be checked for usage of deprecated APIs.](https://react.dev/reference/react/StrictMode#fixing-deprecation-warnings-enabled-by-strict-mode)

## Fixing bugs found by double rendering in development

[React assumes that every component you write is a pure function.](https://react.dev/learn/keeping-components-pure) This means that React components you write must always return the same JSX given the same inputs (props, state, and context).

This includes:

- Your component function body (only top-level logic, so this doesn’t include code inside event handlers)
- Functions that you pass to [`useState`](https://react.dev/reference/react/useState), [`set` functions](https://react.dev/reference/react/useState#setstate), [`useMemo`](https://react.dev/reference/react/useMemo), or [`useReducer`](https://react.dev/reference/react/useReducer)
- Some class component methods like [`constructor`](https://react.dev/reference/react/Component#constructor), [`render`](https://react.dev/reference/react/Component#render), [`shouldComponentUpdate`](https://react.dev/reference/react/Component#shouldcomponentupdate) ([see the whole list](https://reactjs.org/docs/strict-mode.html#detecting-unexpected-side-effects))