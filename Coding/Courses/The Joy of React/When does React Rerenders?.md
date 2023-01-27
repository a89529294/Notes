-   The only way to re-render anything in React is to update a state variable by calling a state-setter function (eg. `setCount`).
-   When a component re-renders, it automatically re-renders all of its descendents, including those that take in no props.
-   We can wrap our component with `React.memo` to optimize it, this prevents React from rerendering it when no props have changed. 
```jsx
function Decoration(){
	return <p>decoration<p>
}

export default React.memo(Decoration)
```