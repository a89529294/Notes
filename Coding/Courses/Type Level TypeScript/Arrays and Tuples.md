# Tuples
__Tuples__ are essentially *lists of types*! They can contain zero, one, or many items, and each one can be a completely different type. Unlike unions, types in a tuple are ordered and can be present more than once. _They look just like JavaScript arrays and are their type-level equivalent_. 

```ts
type SomeTuple = ["Bob", 28, true, 28];

type NameOrAge = SomeTuple[0 | 1]; // => "Bob" | 28

type Values = SomeTuple[number]; // "Bob" | 28 | true
```
Notice how `T[number]` filtered out the duplicate. 

## concatenating tuples
```ts
type Tuple1 = [4, 5];

type Tuple2 = [1, 2, 3, ...Tuple1]; // => [1, 2, 3, 4, 5]
```

## named indices
```ts
type User = [firstName:string, lastName:string]
```
Names help **disambiguate** the purpose of values of the same type, which makes them pretty useful. They help us understand the kind of data we are dealing with but they **don't affect** the behavior of **the type-checker** in any way.

## optional indices
```ts
type OptTuple = [string, number?]; // ^ optional index!

const tuple1: OptTuple = ["Bob", 28]; // ✅
const tuple2: OptTuple = ["Bob"]; // ✅
const tuple3: OptTuple = ["Bob", undefined]; // ✅
```

# Arrays
In TypeScript, array types are extremely common. They represent sets of arrays with an **unknown length**. All of their values must share **the same type**, but since this type can be a **union**, they can also represent arrays of **mixed values**

Since all values in an `Array` have the same type, arrays don't contain a ton of type-level information — they're just wrappers around a single type. In that regard, they are very similar to [Records](https://type-level-typescript.com/objects-and-records#records):
```ts
type BooleanRecord = { [k: string]: boolean };
type BooleanArray = boolean[];
```

# Mixing Arrays and Tuples
Since the introduction of [Variadic Tuples](https://github.com/microsoft/TypeScript/pull/39094), we can use the `...` rest element syntax to mix Arrays and Tuples. This allows us to create types representing arrays **with any number of values**, but with a few **fixed types** at specific indices.

```ts
// number[] that starts with 0
type PhoneNumber = [0, ...number[]];

// string[] that ends with a `!`
type Exclamation = [...string[], "!"];

// non-empty list of strings
type NonEmpty = [string, ...string[]];

// starts and ends with a zero
type Padded = [0, ...number[], 0];
```

# Conclusion
we will mainly focus on **object types** and **tuples**. Since they are the type-level equivalents of our good old objects and arrays that we already know so well, we will be able to use them in algorithms we are already familiar with, like recursive loops!