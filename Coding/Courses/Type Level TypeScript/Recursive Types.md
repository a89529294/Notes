```js
// Using JS as a functional language 🌈
const doRepetitiveTask = (some, input) =>
  condition === true
    ? doRepetitiveTask(again, withSomeOtherInput) // <- recursion
    : something;
```

```ts
// 
type DoRepetitiveTask<Some, Input> =
  Condition extends true
    ? DoRepetitiveTask<Again, WithSomeOtherInput>
    : Something
```
**A recursive loop always contains a condition**. If it did not, the loop would never stop and the type-checker wouldn't be happy about your code. That's why the official documentation refers to these types as _Recursive Conditional Types_.

## looping over tuples
First, we need a data structure to loop over. We will start with tuple types which, as you know, are **the type-level equivalent of arrays**. Recursively looping on an array consists of **three steps**:

- **Splitting** the list into two parts: the **first** element and the **rest** of the list.
- **Computing** something using the **first** element.
- **Recursively calling** the function on the **rest** of the list.

```ts
// Columns contain lists of values
type Column = {
	name: string;
	values: unknown[];
};

// A table is a non-empty list of columns
type Table = [Column, ...Column[]];

// `UserTable` is a subtype of `Table`:
type UserTable = [
	{ name: "firstName"; values: string[] },
	{ name: "age"; values: number[] },
	{ name: "isAdmin"; values: boolean[] }
];

const users:UserTable= [
	{ name: "firstName", values: ["Gabriel", "Bob", "Alice"] },
	{ name: "age", values: [29, 43, 31] },
	{ name: "isAdmin", values: [true, false, false] },
];

type GetColumn<List, Name> = 
List extends [infer First, ...infer Rest]
? First extends { name: Name, values: infer Values }
? Values
: GetColumn<Rest, Name>
: undefined;

const getColumn = <T extends Table, CN extends string>(table: T, columnName: CN): GetColumn<T, CN> => {
	return table.find(c => c.name === columnName)?.values as GetColumn<T, CN>
}

const firstNames = getColumn(users, "firstName");
// We would like `firstNames` to be inferred as a `string[]`

const isAdmins = getColumn(users, "isAdmin");
// and `isAdmins` to be inferred as a `boolean[]`
```

### map loops
```ts
type Names = ToNames<[
  { id: 1; name: "Alice" },
  { id: 2; name: "Bob" }
]>;
// => ["Alice", "Bob"]

type ToNames<List> =
  List extends [infer First, ...infer Rest]
    ? [GetName<First>, ...ToNames<Rest>]
    : [];

type GetName<User> =
  User extends { name: infer Name } ? Name : "Anonymous";
```
the `GetName<First>` is the only custom part

### filter loops
```ts
type Numbers = OnlyNumbers<[1, 2, "oops", 3, "hello"]>;
// => [1, 2, 3]

type OnlyNumbers<List> =
  List extends [infer First, ...infer Rest]
    ? First extends number
      ? [First, ...OnlyNumbers<Rest>]
      : OnlyNumbers<Rest>
    : [];
```
The `number` in `First extends number` is the only custom part

### reduce loops
```ts
type User = FromEntries<[
  ["name", "Gabriel"],
  ["age", 29]
]>;
// => { name: "Gabriel"; age: 29 }

type FromEntries<Entries, Acc = {}> =
  /*                          👆
      `Acc` is optional, with a `{}` default value
                                                    */
  Entries extends [infer Entry, ...infer Rest]
    ? FromEntries<
        Rest,
        Entry extends [infer Key, infer Value]
          ? Acc & { [K in Key]: Value }
          : Acc
      >
    : Acc;
```
generic form
```ts
type SomeReduce<Tuple, Acc = /* ... 📦 initial value */> =
  Tuple extends [infer First, ...infer Rest]
  ? SomeReduce<Rest, /* ... 🤖 logic */>
  : Acc;
```

## recursion and type constraints
Type constraints do not play nicely with conditional types. Variables declared with `infer` **do not inherit** the **constraint** of their parent type:
```ts
type User = { name: string };

type ToNames<List extends User[]> =
  // Expects a list of users 👆
  List extends [{ name: infer Name }, ...infer Rest]
    ? [Name, ...ToNames<Rest>]
    /*                  ~~~~
         ❌ Type 'Rest' does not satisfy
            the constraint 'User[]'.       */
    : [];
```

There are two solutions:
1. Adding a constraint to out `infer` type variable
```ts
type User = { name: string };

type ToNames<List extends User[]> =
  List extends [
    { name: infer Name },
    ...infer Rest extends User[] // <- constraint
  ]
    ? [Name, ...ToNames<Rest>] // ✅
    : [];
```
2. Inferring constraints with conditional types
```ts
type ToNames<List extends User[]> =
  List extends [{ name: infer Name }, ...infer Rest]
    ? [
        Name,
        ...ToNames<Rest extends User[] ? Rest : never> // ✅
      ]
    : [];

// ToNames still works as expected:
type Names = ToNames<[
  { id: 1; name: "Alice" },
  { id: 2; name: "Bob" }
]>;
// => ["Alice", "Bob"] 
```

All in all, both of these options make the code more verbose. Keep in mind _that not using a constraint is often a viable option too_. I personally tend to only add constraints when I need to use some syntax that isn't available for all types like the `...` spread syntax, which requires an `any[]` constraint.

## summary
1. In Type-Level TypeScript loops are defined **recursively** and not imperatively.
2. Any imperative loop can be **rewritten** as a recursive one.
3. To loop over a tuple type, you always perform the **3 same steps**: **split** the list, **use** the first element and **recurse** on the rest of the list.
4. Type constraints can be challenging to use with recursion, but there are ways to make them work!

