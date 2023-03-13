It only works inside the condition of a conditional type, and it can only infer generic type parameters.
```ts
type ArrayContents<T> =
  T extends Array<infer ElementType>
  ? ElementType
  : never;

const n: ArrayContents<Array<string>> = 'one';

  
type OurReturnType<Func> =
	Func extends (...args: any) => infer Return
	? Return
	: never;
	
const add = (a:number, b:number) => a + b

const a: OurReturnType<typeof add> = 1;
```