1. Google fonts
2. https://fontsource.org/
3. Manual 

## manual
1. convert `.otf/.ttf` files to web fonts using [fontsquirrel](https://www.fontsquirrel.com/tools/webfont-generator).
2. Tell the browser we want to use a web font
```css
@font-face {
	font-family: 'Wotfard';
	src: url('/fonts/wotfard-regular.woff2') format('woff2');
	font-weight: 400;
	font-style: normal;
}

@font-face {
	font-family: 'Wotfard';
	src: url('/fonts/wotfard-medium.woff2') format('woff2');
	font-weight: 500;
	font-style: normal;
}

/* for variable fonts */
font-weight: 300 900;
```
This associates a set of *declarations* with a font file. e,g. `font-family: 'Wotfard'` + `font-weight: 400` + `font-style: normal` means we want the file specified in `src`. 

## dowloading variable fonts on google
```
https://fonts.googleapis.com/css2?family=Piazzolla:ital,opsz,wght@0,8..30,100..900;1,8..30,100..900&display=swap
```