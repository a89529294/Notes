We've discovered that types represent **sets of values**. Just like sets, types can include other types and we call this relationship **sub typing**.

The definitive answer is that **objects with more properties are assignable to objects with fewer properties**, but in contexts where **objects are defined inline**, TypeScript has **extra rules** to make sure we don't mistakenly assign props that we couldn't use afterward because our types would forbid us to do so.

This means that you have absolutely **no guarantee** that an object of some type **does not contain** extra props. An object type is the set of objects with **at least** all properties it defines. 
This is why `Object.keys(...)` returns a `string[]` and not a `(keyof Obj)[]`.

## Reading Property Type
```ts
type User = { name: string; age: number; isAdmin: boolean };

// both give string | number
type NameOrAge = User["name" | "age"];
type NameOrAge = User["name"] | User["age"];
```
The **real reason** why it's possible to read several properties at once using a union type is because the **type** level expression `User["name"]` and the value level expression `user["name"]` **work differently**. Instead of finding the key equal to `"name"` in the type `User`, TypeScript tries to find **every key** in `User` that is **assignable** to the type `"name"`.

If we write `User["name" | "age"]`, TS will find all keys assignable to the type `"name" | "age"` and return the union of their value types.

## `keyof` and `ValueOf`
```ts
type User = {
  name: string;
  age: number;
  isAdmin: boolean;
};

type Keys = keyof User; // "name" | "age" | "isAdmin"
type UserValues = User[keyof User]; //  string | number | boolean

type ValueOf<T> = T[keyof T];
type UserValues2 = ValueOf<User>; //  string | number | boolean
```

## keyof unions and intersections
```ts
keyof (A & B) = (keyof A) | (keyof B)

keyof (A | B) = (keyof A) & (keyof B)
```

## records
Just like Object types, Records also represent sets of objects. The difference is that **all keys** of a record must share **the same type**.
```ts
	type RecordOfBooleans = { [key: string]: boolean };
type RecordOfBooleans = Record<string, boolean>; 

RecordOfBooleans[string] // boolean
```

We can also pass in union type
```ts
type InputState = Record<"valid" | "edited" | "focused", boolean>;
type InputState = { [Key in "valid" | "edited" | "focused"]: boolean };
type InputState = { valid: boolean; edited: boolean; focused: boolean };
```