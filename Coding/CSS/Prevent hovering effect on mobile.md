- In *tailwind.config.js*
```js 
/** @type {import('tailwindcss').Config} */

module.exports = {
	content: [
		"./pages/**/*.{js,ts,jsx,tsx}",
		"./components/**/*.{js,ts,jsx,tsx}",
		"./util/**/*.{js,ts,jsx,tsx}",
	],
	theme: {
		extend: {
			screens: {
				"hover-hover": { raw: "(hover: hover)" },
					 },
			},
   plugins: [],
};
```
`hover-hover` is a media query that tells you whether you are on a device that is capable of being hovered over, e.g. laptop.
- On any element instead of `hover:bg-black` use `hover-hover:hover:bg-black`. Now hover effect will only be applied on any device that is capable of beign hovered over.