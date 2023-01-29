- `null` should be used for intentionally missing data; `undefined` should be reserved for unintentionally missing data.
- *Numbers* in programming languages have **limited precision**. 
	- Scanners usualy distinguish between 16 million colors. If you scan a photo with two colors that are close enought you might get the same color!
	- Same thing happens for numbers in JS, there are only 18 quintillion of them. Whereas in real life you have an infinite amount of them.
	- Imagine all of the JS numbers on an axis, the closer they are to zero, the more precision numbers have, the closer they sit to each other.
	- Any **whole** numbers between `Number.MIN_SAFE_INTEGER` and `Number.MAX_SAFE_INTEGER` are exact. This is why `10 + 20 === 30`.
	- However, when we write `0.1` or `0.2` we get the closest available numbers in JS. Most of the time they will be close enough but sometimes you get `0.1 + 0.2 === 0.30000000000000004`
	- `NaN`, `Infinity`, `-Infinity`, `-0`. These are special numbers.

``` js
let scale = 0;
let a = 1 / scale; // Infinity
let b = 0 / scale; // NaN
let c = -a; // -Infinity
let d = 1 / c; // -0
```

- *BigInts* is used to represent large integers with precision. There are an *infinite* amount of them, just like integers in real life.
```js
let max_safe_int = Number.MAX_SAFE_INTEGER; // 9007199254740991
max_safe_int + 1; // 9007199254740992
max_safe_int + 2; // 9007199254740992
// the above both evaluate to the same number

let big_int = 9007199254740991n; // adding n 
big_int + 1n; // 9007199254740992n
big_int + 2n; // 9007199254740993n
// we see that both expressions are accurate now
```

- All conceivable *string values* already exist from the beginning—one value for every distinct string, like *BigInts*.
- *Symbols* serve a similar purpose to door keys: they let you hide away some information inside an object and control which parts of the code can access it.

###### Summary
Remember *primitive values* are immutable and unique. 