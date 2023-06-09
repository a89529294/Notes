When *conditional types act on a generic type*, they become _distributive_ when given a union type.

```ts
type MyExclude<Original , ToExclude> = Original extends ToExclude ? never : Original
```

if `Original` is a union type `string | number`, TS does the following pseudo code, each block is equivalent
```
MyExclude<string | number, number> 

(string extends number ? never : string ) | 
(number extends number ? never : number)

string | never

string
```