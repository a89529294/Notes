- By default React uses the *referential identity of the function* itself and the components *position* within its parent.
- You can *specify a key* instead of using position.

```jsx
function ComponentA(){return <div>Component A</div>}

// render 1
function App(){
	return <div>
		<ComponentA />  
	</div>
}

// render 2
function App(){
	return <div>
		<span>hi</span>
		<ComponentA />
	</div>
}
```
Here `<ComponentA />` was unmounted and then remounted because its position changed.

```jsx
function ComponentA(){return <div>Component A</div>}

// render 1
function App(){
	return <div>
		<ComponentA key='1' />  
	</div>
}

// render 2
function App(){
	return <div>
		<span>hi</span>
		<ComponentA key='1' />
	</div>
}
```
Here `<ComponentA />` will *Not* be unmounted because the function `ComponentA` is referentially identical *and* we used the same key.