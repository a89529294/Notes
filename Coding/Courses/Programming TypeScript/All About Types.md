![[Pasted image 20230503180129.png]]
What is a **type**? It is a *set of values and what you can do with them*.

## type literal
A type that *represents a single value* and nothing else.

## structural typing === duck typing
A style of programming where you just care that an *object has certain properties*, and not what its name is (`nominal typing`). Also called _duck typing_ in some languages.

## index signature
`[key: T] : U` 
The way to read this is,"For this object, all keys of type `T` must have values of type `U`."
There is one rule to keep in mind for index signatures: the index signature key’s type (`T`) must be assignable to either `number` or `string`.

## type union and intersection
a value with a *union type* (`|`) isn’t necessarily one specific member of your union; in fact, it *can be both members* at once!

## any
`any` is the set of _all_ values, and you can do _anything_ with `any`.

## unknown
Like `any`, it represents any value, but TypeScript won’t let you use an `unknown` type until you refine it by checking what it is.

## tuple
Tuples are subtypes of `array`. They’re a special way to type arrays that have fixed lengths, where the values at each index have specific, known types.
Unlike most other types, *tuples have to be explicitly typed* when you declare them.
```ts
// optional elements in tuple
let trainFares: [number, number?][] = [
  [3.75],
  [8.25, 7.70],
  [10.50]
]

// equivalent to above
let moreTrainFares: ([number] | [number, number])[]

// A list of strings with at least one element
let friends: [string, ...string[]] = ['Sara', 'Tali', 'Chloe', 'Claire']
```

## readonly arrays and tuples
```ts
type A = readonly string[]           // readonly string[]
type B = ReadonlyArray<string>       // readonly string[]
type C = Readonly<string[]>          // readonly string[]

type D = readonly [number, string]   // readonly [number, string]
type E = Readonly<[number, string]>  // readonly [number, string]
```
