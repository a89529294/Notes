In [Types Are Just Data](https://type-level-typescript.com/types-are-just-data), we discovered that types were really **sets of values**, and that union types were data structures **joining several sets** together to form **larger sets**.

## Union Type Multiverse
Since unions do not represent **a single runtime _thing_** but rather **different versions** of the runtime **reality**, I like to visualize them as a superposition of states. It's like each member of a union type was a different parallel **_universe_**.

My runtime `trafficLight` variable will only ever be in one of the three `TrafficLight` states, but from the perspective of the type-checker, all of them exist at the same time.
```ts
type TrafficLight = "green" | "orange" | "red";

const trafficLight: TrafficLight = "green";
```

In our Union Type Multiverse, **everything that can happen happens**. Every time we use a union type in a type-level expression: It's like all possible branches were occurring separately
```ts
type ShouldStop = { green: "no"; orange: "yes"; red: "yes" };

type T = ShouldStop["green" | "orange" | "red"]; 
// type T = "no" | "yes"
```
As a result, we get back another union type that represents this new superposition of states.

At the type level, they're **non-deterministic values**. Every time we use a union inside an expression, it turns it into a non-deterministic one. These expressions can return an arbitrary number of results. This is what gives union types their **distributive nature**.

## The Distributive Nature of Union Types
Template literal types *distribute over union types*:
```ts
type T1 = `x ${"a" | "b" | "c"}`;
// <=>
type T2 = `x ${"a"}` | `x ${"b"}` | `x ${"c"}`;
// both "x a" | "x b" | "x c"
```

Accessing object properties also _distributes over union types_:
```ts
type T1 = User["name" | "age"];
// <=>
type T2 = User["name"] | User["age"];
```

Conditional types _distribute_ over union types
```ts
type IsString<T> = T extends string ? "yes" : "no";

type T = IsString<"a" | 2>; // "yes" | "no"    
```