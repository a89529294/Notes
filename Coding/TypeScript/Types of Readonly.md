## readonly property
```ts
interface SomeType {
	readonly prop: string
}

const obj: SomeType = { prop: 'hi'}
obj.prop = 'bye' // not allowed!
```
readonly `prop` cannot be reassgined, however if it holds an object it still can be mutated.

## ReadonlyArray
```ts
const array:ReadonlyArray<string> = ['1','2'] 
const array2:readonly string[] = ['3,','4']
// above are the same

array.push('3') // not allowed!
```
arrays with type `ReadonlyArray<T>` cannot be mutated.