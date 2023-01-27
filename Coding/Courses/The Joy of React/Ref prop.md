You can pass in a function to a ref prop on a native element like so
```jsx
<div ref={(arg)=>console.log(arg)}>...</div>
```
The `arg` will be the underlying DOM node.

https://beta.reactjs.org/reference/react-dom/components/common#ref-callback