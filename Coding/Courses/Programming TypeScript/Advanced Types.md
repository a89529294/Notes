## subtype & supertype
If you have two types `A` and `B`, and `B` is a *subtype* of `A`, then you can safely use a `B` anywhere an `A` is required.

## subtyping functions
A function A is a *subtype* of function B if A has the *same or lower arity* (number of parameters) than B and:

1. A’s this type either isn’t specified, or is >: B’s this type.
2. Each of A’s parameters is >: its corresponding parameter in B.
3. A’s return type is <: B’s return type.
 
## assignability
For _non-enum types_—like arrays, booleans, numbers, objects, functions, classes, class instances, and strings, including literal types—`A` is assignable to `B` if either of the following is true:
1. A is a *subtype* of B
2. A is `any` 

## type widening
In general, TypeScript will be *lenient when inferring your types*, and will err on the side of inferring a more general type.

## conditional types
```ts
type IsString<T> = T extends string 
  ? true 
  : false 

type A = IsString<string> // type A = true
type B = IsString<number> // type B = false
```
*Conditional types* aren’t limited to type aliases. *You can use them almost anywhere you can use a type*: in type aliases, interfaces, classes, parameter types, and generic defaults in functions and methods.

## distributive conditionals
```ts
(string | number) extends T ? A : B 
// is equivalent to the following
(string extends T ? A : B) | (number extends T ? A : B)

type ToArray<T> = T[]
type A = ToArray<number> // type A = number[]
type B = ToArray<number | string> // type A = (number | string)[]

type ToArray2<T> = T extends unknown ? T[] : T[]
type C = ToArray2<number> // type C = number[]
type D = ToArray2<number | string> // type D = number[] | string[]

type Without<T, U> = T extends U ? never : T
type E = Without<number | string, string> // type E = number
```

## mapped types
**Basic Mapped Types**: transforming property types
```ts
type MappedType<T> = {  
	[K in keyof T]: /* transformed type based on T[K] */;  
};
```
`T` is a generic type parameter, and `K` is a type variable iterating over the keys of `T`. The `keyof` keyword produces a union of the keys of `T`, and the `in` keyword is used to iterate over those keys.

**Key Remapping**: transforming keys based on the original keys
```ts
type KeyRemappedType<T> = {  
	[K in keyof T as /* transformed key based on K */]: T[K];  
};

interface OriginalInterface {  
	key1: string;  
	key2: number;  
	key3: boolean;  
}  
  
type NewInterface = {  
	[K in keyof OriginalInterface as `new_\${K}`]:          OriginalInterface[K];  
};  
  
const newObj: NewInterface = {  
	new_key1: 'Hello',  
	new_key2: 42,  
	new_key3: true,  
};

type DropKeysWithFalseyValues<T> = {
	[K in keyof T as T[K] extends null | undefined ? never : K ]: T[K]
}
```
We are still iterating over the keys of `T` just that we are also transforming the key itself at the same time. 

## definite assignment assertion
```ts
let userId!: string

userId.toUpperCase() // no error because of the ! 
```
