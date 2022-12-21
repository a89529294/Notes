A **type assertion** tells TypeScript you have performed any special checks that you need before calling the statement.

It performs *no special checking* or restructuring of data. It has *no runtime impact* and is used *purely by the compiler*.

```ts
(randomValue as string).toUpperCase();
```

*Type Guards*
```ts
typeof s === 'string'
typeof n === 'number'
typeof b === 'boolean'
typeof undefined === 'undefined'
typeof f === 'function'
Array.isArray(a) 
```