Three kinds of equalities
- **Strict Equality:** `a === b` (triple equals).
- **Loose Equality:** `a == b` (double equals).
- **Same Value Equality:** `Object.is(a, b)`.

## Same Value Equality
Fits perfectly with our mental model. Just one thing, you can compare value with `Object.is(a,b)`, including primitive values.

## Strict Equality
Same as *same value equality*. Except for two cases
- `NaN === NaN` is `false`, although they are the same value.
- `0 === -0` is `true`, although they are different values.

## Loose Equality
The only use case worth knowing is `x == null` is equivalent to `x === null || x === undefined`
```js
if (x == null) {}
if (x === null || x === undefined) {}
// the same
```

### Misc
Three ways of detecting `NaN`
- `Number.isNaN(value)`
- `Object.is(value,NaN)`
- `NaN !== value`, since `NaN` is the only value not equal to itself using `===`.