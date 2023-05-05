When are `Generics` bound?
We bound `<T>` to the *function call signature*, therefore TypeScript will bind a concrete type to `T` when we actually *call* a function of type `Filter`.  
```ts
type Filter = <T>(array: T[], f: (item: T) => boolean) => T[]
const filter: Filter = (array, f) => {
	let result = []
	for (let i = 0; i < array.length; i++) {
		let item = array[i]
		if (f(item)) {
			result.push(item)
		}
	}
	return result
}
console.log(filter([1, 2, 3, 4], _ => _ < 3))
```
If we move `<T>` to the type alias `Filter`, TypeScript would require us to bind a type explicitly when we used `Filter`
```ts
type Filter<T> = (array: T[], f: (item: T) => boolean) => T[]
const filter: Filter<number> = (array, f) => {
...
}
console.log(filter([1, 2, 3, 4], _ => _ < 3))
```

The first option is a lot more flexible. Using the second option if we were to apply `filter` to an array of strings we need to update `const filter: Filter<string>`.

Generally, TypeScript will bind concrete types to your generic when you use the generic: for *functions*, it’s when you *call* them; for *classes*, it’s when you *instantiate* them (more on that in [“Polymorphism”](https://learning.oreilly.com/library/view/programming-typescript/9781492037644/ch05.html#class-generics)); and for *type* *aliases* and *interfaces* (see [“Interfaces”](https://learning.oreilly.com/library/view/programming-typescript/9781492037644/ch05.html#interfaces)), it’s when you *use* or implement them.

## Misc
- TypeScript only uses the *types of a generic function’s arguments* to *infer* a generic’s type
- 
