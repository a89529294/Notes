- Put this somewhere in the root
```js
function calculateViewHeight() {
	let vh = window.innerHeight * 0.01;
	document.documentElement.style.setProperty("--vh", `${vh}px`);
}

useEffect(() => {
	calculateViewHeight();
	window.addEventListener("resize", calculateViewHeight);
	return () => window.removeEventListener("resize", calculateViewHeight);
}, []);
```

- Tell *Tailwind* to use the new `vh`, put this in the file *tailwind.config.js* in `theme.extend` object.
```js
height: (theme) => ({
	auto: "auto",
	...theme("spacing"),
	full: "100%",
	screen: "calc(var(--vh) * 100)",
}),

minHeight: (theme) => ({
	0: "0",
	...theme("spacing"),
	full: "100%",
	screen: "calc(var(--vh) * 100)",
}),
```