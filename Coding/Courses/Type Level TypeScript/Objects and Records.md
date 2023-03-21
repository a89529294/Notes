We've discovered that types represent **sets of values**. Just like sets, types can include other types and we call this relationship **subtyping**.

```ts
type User = { name: string; age: number; isAdmin: boolean };

// both give string | number
type NameOrAge = User["name" | "age"];
type NameOrAge = User["name"] | User["age"];
```
If we write `User["name" | "age"]`, TS will find all keys assignable to the type `"name" | "age"` and return their value types.

## keyof and ValueOf
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