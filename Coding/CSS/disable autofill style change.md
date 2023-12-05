```css
/* Disable autofill style change */
/* supposed to work on firefox, but doesn't */
input:autofill,
input:autofill:hover,
input:autofill:focus,
input:autofill:active {
	transition: color 5000s ease-in-out 0s, background-color 5000s ease-in-out 0s !important;
}

/* works on chrome */
input:-webkit-autofill,
input:-webkit-autofill:hover,
input:-webkit-autofill:focus,
input:-webkit-autofill:active {
	transition: color 5000s ease-in-out 0s, background-color 5000s ease-in-out 0s !important;
}
```