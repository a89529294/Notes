## Function Overloading
```ts
function task(name:string, dependencies:string[]):void
function task(name:string, callback:()=>void):void
function task(name:string, dependencies:string[], cxallback:()=>void):void
function task(name:string, param2: string[] | (()=>void), param3? : ()=>void){
	// implementation
}
```
- TypeScript only picks up the _declarations before the actual implementation_ as possible types.
- TypeScript checks if the overloads can be implemented with the implementation signature.
- If you wish to create a standalone function overload type
```ts
type TaskFn = {
(name: string, dependencies: string[]): void;
(name: string, callback: ()=>void): void;
(name: string, dependencies: string[], callback: ()=>void): void;
}
```
