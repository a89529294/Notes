```css
/* Disable autofill style change */
{/* supposed to work on firefox, but doesn't */}
input:autofill,
input:autofill:hover,
input:autofill:focus,
input:autofill:active {
	transition: all 0s 50000s;
}

{/* works on chrome */}
input:-webkit-autofill,
input:-webkit-autofill:hover,
input:-webkit-autofill:focus,
input:-webkit-autofill:active {
transition: all 0s 50000s;
}
```