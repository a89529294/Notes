The key distinction is that a *type alias cannot be reopened* to add new properties whereas an *interface is always extendable*. 
You can only describe a *union or tuple using a type alias*.

```ts
interface A {
	a:string;
}

interface B {
	a:"a"|"b";
}

interface C extends A,B {
	a:"a" | "b"
}
```