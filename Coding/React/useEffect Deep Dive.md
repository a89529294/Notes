## Each render has its own state and props
```jsx
function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```
In this example, `count` is just a number. It’s *not* a magic “data binding”, a “watcher”, a “proxy”, or anything else. 

Whenever we update the state, React calls our component. Each render result “sees” its own `counter` state value which is a _constant_ inside our function.

`<p>You clicked {count} times</p>` **This only embeds a number value into the render output.** That number is provided by React. When we `setCount`, React calls our component again with a different `count` value. Then React updates the DOM to match our latest render output.

The key takeaway is that the `count` constant inside any particular render doesn’t change over time. It’s our component that’s called again — and each render “sees” its own `count` value that’s isolated between renders.

**Every function** inside the component render (including event handlers, effects, timeouts or API calls inside them) *captures the props and state of the render call that defined it*.

## useEffect setup function
`useEffect(setup, dependencies?)`
`setup`: The function with your Effect’s logic. Your setup function may also optionally return a _cleanup_ function. When your component is first added to the DOM, React will run your setup function. *After every re-render with changed dependencies*, React will first run the cleanup function (if you provided it) with the old values, and then run your setup function with the new values. After your component is removed from the DOM, React will run your cleanup function one last time.

## useReducer
When *setting a state variable depends on the current value of another state variable*, you might want to try replacing them both with `useReducer`.

