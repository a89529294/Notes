In Type-level TypeScript, code branching is known as **Conditional Types**. The syntax is very similar to the [Ternary Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator) we use in JavaScript:

_this is the only valid condition type_
`A extends B ? ... : ...`

```ts
type TrueOrFalse = A extends B ? true : false;
/*                 -----------   ----   -----
                      ^          /         \
                 condition    branch     branch
                             if true    if false
          
                   \-------------------------/
                                ^
                        Conditional Type
*/
```

Before the question mark stands a **condition**. It's **always** of the form `A extends B`, which is how you ask _"Is A assignable to B?"_ to the type checker.
_"A is assignable to B"_ means that the set of values defined by the type `B` _includes_ the set of values defined by the type `A`.

## never is a special case
When put on the left side of `extends` in a conditional type, it always evaluates to `never`. 

### example
```ts
type IsMeaningOfLife<N> = N extends 42 ? true : false;

type OK = IsMeaningOfLife<42>; // => true
type KO = IsMeaningOfLife<41>; // => false
```

## type constraint
```ts
type If<A extends boolean, B, C> = A extends true ? B : C;

type a = If<true, number, string>; // number
type b = If<false, {}, []>; // []
```
 `A extends true` is the **condition** of our code branching expression,`A extends boolean` is called a **type constraint**.

The `extends` keyword is always about assignability. In a **conditional type**, we use `extends` to ask the question _"Is A assignable to B?"_ to the type-checker. In a **type constraint**, however, `extends` is an affirmation: _"A must be assignable to B."_

## narrowing input types with type constraints
Without the `extends string` TypeScript will infer the type of `user1` and `user2` to be `{name: string}`. 
```ts
const createUser = <S extends string>(name: S) => ({ name });

const user1 = createUser("Gabriel");
//      ^? { name: "Gabriel" } 🎊

const user2 = createUser("Alice");
//      ^? { name: "Alice" } 🎈
```

```ts
const inferAsTuple = <
  T extends [unknown, ...unknown[]]
  //                  👆
  //   We use a non-empty array of unknown values.
>(tuple: T) => tuple;

const t1 = inferAsTuple([1, 2]);
//    ^? [number, number]
// instead of number[]

const t2 = inferAsTuple(["a", 2, true]);
//    ^? [string, number, boolean]
// instead of (string | number | boolean)[]
```

When TypeScript sees a constraint on a type parameter, it will try to infer it to a **subtype** of this constraint!

## nesting conditions
```ts
type GetColor<I> =
    I extends 0 ? "black"
  : I extends 1 ? "cyan"
  : I extends 2 ? "magenta"
  : "white";
```

We can do the following if we wish to branch on a union of literals
```ts
type GetColor<I extends 0 | 1 | 2 | 3> = {
  0: "black";
  1: "cyan";
  2: "magenta";
  3: "white";
}[I];
```

## pattern matching
Using pattern matching, we can also branch on **several type parameters at once**. We only need to wrap them in a data structure first, like a [**Tuple**](https://type-level-typescript.com/arrays-and-tuples#tuples):
```ts
type Plan = "basic" | "pro" | "premium";
type Role = "viewer" | "editor" | "admin";

// branching on several types by wrapping
// them in a tuple:
type CanEdit<P extends Plan, R extends Role> =
  [P, R] extends ["pro" | "premium", "editor" | "admin"]
  ? true
  : false;

type T1 = CanEdit<"basic", "editor">; // => false
type T2 = CanEdit<"premium", "viewer">; // => false
type T3 = CanEdit<"pro", "editor">; // => true
type T4 = CanEdit<"premium", "admin">; // => true
```

## infer
The `infer` keyword is the real **superpower** of Conditional Types. It enables us to **declare a type variable** by **destructuring** the type on the left-hand side of `extends`:
```ts
type GetRole<User> =
  User extends { name: string; role: infer Role }
    ? Role //                          ^ new! 🤔
    : never;

type T1 = GetRole<{ name: "Gabriel"; role: "admin" }>;
// => 'admin'

type T2 = GetRole<{ role: "user" }>;
// => `never` because the input type doesn't have a `name` property.
```
Here, the function `GetRole` checks if `User` is assignable to `{ name: string; role: any }`. If it is, we declare a variable `Role` that contains the type of the `role` property and we return it. If `User` isn't assignable to this pattern, we return the `never` type.
- the `infer` keyword can only be used in the rhs of extends
- the inferred variable, e.g. `Role` can only be used in the truthy branch

### infer with tuple types
```ts
type Tail<Tuple> = Tuple extends [any, ...infer Rest] ? Rest : [];

// `Tail` is the type-level equivalent of:
const tail = ([first, ...rest]) => rest;

type T1 = Tail<["alpha", "beta", "gamma"]>; // => ["beta", "gamma"];
type T2 = Tail<["alpha"]>; // => []
type T3 = Tail<[]>; // => []
```

### infer with function types
```ts
type IsEqual = (a: number, b: number) => boolean;
```
At the type level, **function types are data structures too**!
They are essentially wrappers around a Tuple representing the list of arguments bundled with an arbitrary return type
```ts
type Parameters<F> = F extends (...params: infer P) => any ? P : never;

type Fn = (name: string, id: number) => boolean;

type T1 = Parameters<Fn>; // => [name: string, id: number]
```

### infer with custom generics
The `infer` keyword can also be used _in place of a generic type parameter_.
```ts
type SetValue<S> = S extends Set<infer V> ? V : never;

type T1 = SetValue<Set<number>>; // => number
type T2 = SetValue<Set<string>>; // => string

// custom generic
type MyOwnGeneric<A, B> = { content: A; children: B[] };

type ExtractParams<S> = S extends MyOwnGeneric<infer A, infer B>
? [A, B] : never;

type T1 = ExtractParams<MyOwnGeneric<number, boolean>>;
// => [number, boolean]

type T2 = ExtractParams<MyOwnGeneric<string[], unknown>>;
// => [string[], unknown]
```

### variable assignment
```ts
type Fn<I> = SuperHeavyComputation<I> extends infer Result
  //                                     ^  🤯  ^ 
  ? [Result, Result, Result]
  : never; // this branch can never be reached
```
We can use `infer` directly after `extends`. This will have the effect of assigning the result of `SuperHeavyComputation<I>` to a variable. The downside is that we need to declare an "else" code branch even though we know it will never be reached because any type is assignable to `infer Result`.

## Summary
- At the type level, we use **Conditional Types** for code branching.
- Conditional types **must be** of the form `A extends B ? T : F`.
- `A extends B` means _"A is assignable to B"_.
- We can also use `extends` to declare a [type constraint](https://type-level-typescript.com/members/conditional-types#type-constraints-with-extends) on a type parameter. [[##narrowing input types with type constraints]]
- The `infer` keyword lets us **assign a variable** by **extracting** a piece from a data-structure type.
- `infer` can only be used within a conditional type, on the right-hand side of `extends`.
- Even though conditional types look like value-level ternaries, they are much more powerful because they let us **pattern-match** on types.