Function *default parameters* are evaluated when the function is called, not when it is defined. So you can reference other varaibles, even other arguments.
```js
function f (a, b=a){...}
```