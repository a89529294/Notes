## CSS custome properties
- They are *inheritable*
- `var(--my-color, 'red');` uses color red as fallback.

## Calc function
```css
.something {
	width: calc(50% + 32px);
}
```
- notice we can mix units
- we can use four operators `+`, `-`, `*`, `/`

## Viewport units
- these are `length` units, so can be used anywhere `length` can be used.
- `vw` refers to the viewport width _not counting the scrollbar_ on desktop.
- the `vh` unit **always refers to the largest possible height**.
- On *mobile*, *viewport height* *changes* once you start sliding.
- `vmin` will refer to the _shorter dimension_, while `vmax` refers to the longer one. e.g. on portrait mode, `vmin` refers to `vw` and `vmax` refers to `vh`.
- New viewport units
	- `svh` Small Viewport Height
	- `lvh` Large Viewport Height
	- `dvh` Dynamic Viewport Height
	- The `lvh` unit works like the `vh` unit does; it always refers to the _full_ viewport height, once the browser UI has shrunk down.
	`svh` always refers to the _smaller_ height, the height that first shows when the page loads.
	Finally, `dvh` will dynamically adjust as the viewport height changes. This is the way our `height: 100%` alternative works.

## clamp function
```css
/* Method 1 */
.column {
	min-width: 500px;
	width: 65%;
	max-width: 800px;
} 

/* Method 2 */
.column {
	width: clamp(500px, 65%, 800px);
}

/* Method 3 */
.column {
	width: clamp(500px, 65%, 800px);
	max-width: 100%;
}
```
- `method 1` and `method 2` are functionally *identical*.
- The advantage of `clamp` is we free up `min-width` & `max-width`.
- In `method 3` we are essentially applying two `max-width`, now `.column` cannot be larger than 800px or 100%. i.e. it needs to satisfy both.
- Note that `clamp` is a *value* not a *property*! It can be applied to used with a lot of *properties*.

## min and max
```css
.box {
    /* it evaluates to the smaller one */
	padding: min(32px, 5vw);
	/* it evalues to the larger one */ 
	width: max(100px, 100%);
}
```