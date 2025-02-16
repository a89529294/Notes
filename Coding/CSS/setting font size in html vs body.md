- `rem` in html refers to browsers font size setting. If unchanged it is 16px.
- `rem` in anywhere else refers to font size set in the html element.

For example, if you set (browser font size setting is 16px)
```css
html {
	font-size: 2rem; /* here 1 rem is equal to browser setting */
}

p {
	font-size: 1rem; /* here 1 rem is equal to font size set in html */
}
```

then p elements will have a font size of 32px.

However if you set
```css
body {
	font-size: 2rem;
}

p {
	font-size: 1rem; /* 16px because font size of html is unchanged */
}
```

here p elements will have a font size of 16px