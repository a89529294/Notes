- Only two values are required
	1. the name of the property we wish to animate
	2. the duration of the animation
```css
.btn {
	transition: transform 250ms;
}

.bth:hover {
	transform: translateY(-10px);
}
```
- If you plan on animating multiple properties, you can pass it a comma-separated list: `transition: transform 250ms, opacity 400ms`;

## Timing functions
`ease-out`
- starts fast, ends slow
- It's most commonly used when something is entering from off-screen (eg. *a modal appearing*).
`ease-in`
- starts slow, ends fast
- pretty much exclusively useful for animations that end with the element offscreen or invisible (eg. _a modal disappearing_).
`ease-in-out`
- starts slow, speeds up ,ends slow
- most useful for anything that happens in a *loop* (eg. an element fading in and out, over and over).
`ease`
- similar to `ease-in-out`, buy asymetrical, end is slower than start.
- default value.

## delay
```css
/* rule 1 */
.dropdown {
	opacity: 0;
	transition: opacity 400ms;
	transition-delay: 300ms;
}

/* rule 2 */
.dropdown-wrapper:hover .dropdown {
	opacity: 1;
	transition: opacity 100ms;
	transition-delay: 0ms;
}
```
- when hovering both `rule 1` and  `rule 2` applies. This means the transition has a duration of `100ms` with `0ms` delay.
- when leaving only `rule 1` applies. This means the transition has a duration of `400ms` and a delay of `300ms`.