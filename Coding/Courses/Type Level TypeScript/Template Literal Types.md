## Template Literals and Primitive Types
```ts
type FirstName = "Gabriel";

type Gabriel = `${FirstName} ${string}`; // `Gabriel ${string}`
```

`` `Gabriel ${string}` `` is the **set** of all string literals that **start with** `"Gabriel "`

```ts
const name1: Gabriel = "Gabriel Vergnaud"; // ✅
const name2: Gabriel = "Gabriel Fauré"; // ✅
const name3: Gabriel = "Gabriel "; // ✅ because "" is a string.
const name4: Gabriel = "Who's there?"; // ❌
const name5: Gabriel = "Hello Gabriel"; // ❌
```

You can use them to create **patterns** containing `numbers` or `booleans` too.

```ts
type Age = `I was born in ${number}.`;

const age1: Age = "I was born in 1993."; // ✅
const age2: Age = "I was born in 3.141592."; // ✅
const age3: Age = "I was born in a galaxy far, far away..."; // ❌
// "a galaxy far, far away..." is not a number!
```

This can be handy to make sure our functions receive strings of the expected format:

```ts
declare function ping(localDomain: `localhost:${number}`): void;

ping("localhost:3000"); // ✅
ping("localhost:8080"); // ✅
ping("localhost:three-thousand"); // ❌
```

Template Literal Types are **more than just a way to concatenate strings**. They behave more like **data structures** containing string fragments and primitive types.


## Template Literals and Union Types
```ts
type Size = "sm" | "md" | "lg";

type ClassName = `size-${Size}`;
// => "size-sm" | "size-md" | "size-lg"
```

Each item of this union is interpolated separately, and we get back **the union of their results**!

```ts
type Variant = "primary" | "secondary";
type Size = "sm" | "md" | "lg";

type ButtonStyle = `${Variant}-${Size}`;
// => | "primary-sm"   | "primary-md"   | "primary-lg"
//    | "secondary-sm" | "secondary-md" | "secondary-lg"
```

## Pattern Matching on String Literals
```ts
type GetNameTuple<Name> =
  Name extends `${infer FirstName} ${infer LastName}`
    ? [FirstName, LastName] //    ^
    : never;      /*      notice the space 🪐   */
    
type T1 = GetNameTuple<"Hermione Granger">;
// => ["Hermione", "Granger"]
type T2 = GetNameTuple<"Ron Weasley">;
// => ["Ron", "Weasley"]
```

The string is split after the **first character** in this case!
```ts
type SplitString<Input> =
  Input extends `${infer A}${infer B}`
    ? [A, B] //           ^ no separator 🤔
    : never;

type T1 = SplitString<"some string">;
//   =>   ["s", "ome string"]
type T2 = SplitString<"what">;
//   =>   ["w", "hat"]
```

Turn a string into snake case:
```ts
type Title = 'Hello, Type Level TypeScript Member!';

type Punctuation = '.' | '?' | ',' | '!';

type SnakeCase<S extends string> = Lowercase<RemovePunctuation<SpaceAsUnderscore<S>>>

type SpaceAsUnderscore<S extends string> = 
S extends `${infer First} ${infer Rest}` ? `${First}_${SpaceAsUnderscore<Rest>}` : S

type RemovePunctuation<S extends string, O extends string = ''> =
S extends `${infer First}${infer Rest}` ?
First extends Punctuation ?
RemovePunctuation<Rest, O> :
RemovePunctuation<Rest, `${O}${First}`> :
O;

type Result = SnakeCase<Title>;
```
Note that `RemovePunctuation` we do not split on `Punctuation` since it is a union. Instead we go through each character one by one. _Splitting strings using a union type_ as a separator _doesn't quite work_ as expected.

### Summary
In JavaScript, we use **strings** to encode a **wide range of information**. Our functions often assume that input strings have **a specific structure** that they can interpret. This structure can sometimes be relatively simple (e.g. an object path) but it can also get very complex (e.g. a SQL[1](https://type-level-typescript.com/members/template-literal-types#user-content-fn-1) or a GraphQL query).

Template Literal Types allow us to fully **embrace** this ability to give strings special meanings. They not only let us enforce that our input strings have the correct structure but also enable us to parse them to infer new types.

We've covered many important notions in this chapter, but here are the key takeaways:

1. Template Literal Types can not only be used to **concatenate** literal types together but also to **represent** sets of string literal types with a **specific structure**.
2. **Interpolating a union type** in a template turns it into a **union of templates**.
3. **Conditional types** let us **split** template literals into several parts.
4. **In ambiguous cases**, TypeScript will use the **first occurrence** of your separator to split the string.
5. **Recursive types** let us build type-level **parser** functions.