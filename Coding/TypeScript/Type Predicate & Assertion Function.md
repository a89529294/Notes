```ts
type Fish = {
	swim:()=>void
}
type Bird = {
	fly:()=>void
}
function isFish(pet:Fish | Bird): pet is Fish {
	return !!(pet as Fish).swim
}
```
Note this function must only *accept a single argument* and *return a boolean*.

## Assertion Function
You can only use *traditional function* to define assertion functions. Arrow functions will throw an error.