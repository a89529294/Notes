- `useLayoutEffect` vs. `useEffect`
	- Same api, the only difference is when they are run
	- `useLayoutEffect` runs right after browser updates DOM and right before browser paints the DOM
	- `useEffect` runs right after browser pains the DOM
	- Only use `useLayoutEffect` if the side effect shifts the DOM in a noticable way or you want to gunarantee the side effect in `useLayoutEffect` runs before any `useEffect`
- `useImperativeHandle`
	- Use in combination with `forwardRef` 
	- Main use is attaching some methods or properties that can only be accessed in a child component but you need to access those methods/properties in a parent component. 
	- Wrap your child component in `forwardRef` and return the needed properties in an object using `useImperativeHandle`.
``` js
const ChildComponent = React.forwardRef((props,ref)=>{
	
	React.useImperativeHandle(ref,()=>{
		return {
			method1:()=>{}
			property1: 1
		}
	})
})

const ParentComponent = ()=>{
	const myRef = React.useRef()
	
	return <div>
		<ChildComponent ref={myRef} onClick={()=>ref.current.method1()}/> 
	</div>
}
```
- `useDebugValue`
	- Only use case is to label custom hooks
	``` js
	const useCustomHook = ()=>{
		React.useDebugValue(`hi I am a label`)
	}
```
	- Now in devtool you should see your custom hook labeled.