If the *initial value* is supplied you have to *type* the initial value
```ts
arr.reduce((acc,val)=>...,[])

/* Either way works*/
arr.reduce<string[]>((acc,val)=>...,[])

arr.reduce((acc,val)=>...,[] as string[])
```