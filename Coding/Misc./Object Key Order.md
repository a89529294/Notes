Object keys are always ordered unless it is a number.
When an object has number keys:
	1.  They always come first in the key list.
    2.  They're always sorted numerically.
    3.  They're always converted into strings (`1` becomes `'1'`).

```js
Object.keys({b: 'b', 1: 'one', a: 'a'}) 
// ['1','b','a']
```