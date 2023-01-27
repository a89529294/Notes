```jsx
export const MyContext = React.createContext()

function App(){
	return <MyContext.Provider value={1}>
		<HomePage/>
	</MyContext.Provider>
}
```
1. Create context through `export const MyContext = React.createContext()`
2. Wrap a component with 
   `<MyContext.Provider value={myValue}>...</MyContext.Provider>`
3. Any component in the wrapped component can consume it with
   `const myValue = React.useContext(MyContext)`