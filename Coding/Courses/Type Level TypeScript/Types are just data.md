## Five categories of types
TypeScript provides us with 5 main categories of types: **primitive** types, **literal** types, **data structure** types, **union** types, and **intersection** types.

### Primitive types
All primitive types as a union
```ts
type Primitives = number | string | boolean | null | undefined | bigint | symbol
```

### Literal types
Literal types are "exact" types, which encompass a **single possible value**.
A tiny selection of literal types
```ts
type Literals = 20 | 'Hello' | true | 1000n
```

### Data structure types
In our type-level world, we have four built-in data structures at our disposal: **objects**, **records**, **tuples** and **arrays**.
```ts
type DataStructures = 
| { key1: boolean; key2: number } // object
| { [key: string]: number } // record
| [boolean, number] // tuple
| number[] array
```
-   **Object types** describe objects with a finite set of keys, and these keys contain values of potentially different types.
-   **Record types** are similar to object types, except they describe objects with an unknown number of keys, and all values in a record share the same type. For example, in `{ [key: string]: number }`, all values are numbers.
-   **Tuple types** describe arrays with a fixed length. They can have a different type for each index.
-   **Array types** describe arrays with an unknown length. Just like with records, all values share the same type.

#### Summary
- All types are *sets*. This means no types can contain duplicates.
- *unknown* is the super set. It contains every other type.
- *never* is the empty set. It is a subtype of every other type, meaning you can assign a value of type never to any other type.
```ts
function f():never {throw ''}

const a: string = f()
```
- *any* doesn't respect the laws of set theory, it's both the super type and sub type of every other type.