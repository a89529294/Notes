- When reading `obj.something`, if `obj` doesn’t have a `something` property, JavaScript will look for `obj.__proto__.something`. Then it will look for `obj.__proto__.__proto__.something`, and so on, until it either finds our property or reaches the end of the prototype chain.
- When writing to `obj.something`, JavaScript will usually write to the object directly instead of traversing the prototype chain.
- We can use `obj.hasOwnProperty('something')` to determine whether our object has its _own_ property called `something`.
- We can “pollute” a prototype shared by many objects by mutating it. We can even do this to the Object Prototype—the default prototype for `{}` objects! (But we shouldn’t, unless we’re pranking our colleagues.)
- You probably won’t use prototypes much directly in practice. However, they are fundamental to JavaScript objects, so it is handy to understand their underlying mechanics. Some advanced JavaScript features, including classes, can be expressed in terms of prototypes.

### Object.prototype
All objects created using `{}` has a wire `__proto__` pointing to the `Object.prototype`. This object has various methods including `toString()`, `hasOwnProperty`. 
This is why you can do `({}).toString()` or call `toString()` on any object.
In fact, __almost all objects in javascript__ have `Object.prototype` at the end of their prototype chain.
You can create objects with no `__proto__` using `Object.create(null)`, or simply after creating the object called `obj` set its `__proto__` directly to `null`,
`obj.__proto__ = null;`

### \_\_proto\_\_ vs prototype
By default `prototype` prop only exists on functions, and `__proto__` on objects.
Of course functions are also objects, so `__proto__` also exists on functions.
The purpose for __prototype__ on functions is to set the `__proto__` of objects created by the `new` keyword.
```js
function Donut() {
  this.shape = 'round';
}

Donut.prototype = {
  eat() {
    console.log('Nom nom nom');
  }
};

let donut1 = new Donut(); // __proto__: Donut.prototype
let donut2 = new Donut(); // __proto__: Donut.prototype

donut1.eat();
donut2.eat();
```

