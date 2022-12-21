- *Named functions*/ *function declarations*(functions defined using `function` keyword) are hoisted therefore can be used before their declarations.
- *Anonymous functions*/ *function expressions* are not hoisted therefore must be delcared before they can be used.
	- There are two ways of creating an *anonymous function*, one with `function` keyword but without a name, the other is using an arrow function.
```ts
addTwoNumbers(a,b) // Error, Block-scoped variable 'addTwoNumbers' used before its declaration.
const addTwoNumbers = function (a:number,b:number):number{
	return a + b;
}
```

When a function is called, the TypeScript compiler verifies:
-   A value has been provided for each parameter if required. By default, params are required unless marked as optional.
-   Only parameters that the function requires are passed to it.
-   The parameters are passed in the order in which they are defined in the function.