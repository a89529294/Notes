1. put font files in `public` folder
2. add following to `globals.css`, adjust name, url, etc
```css
@font-face {
  font-family: "Whitney"; 
  src: url("/whitney/whitney-light.woff") format("woff");
  font-weight: 400;
  font-style: normal;
}
```
3. 
	- on body tag put `{{fontFamily: 'Whitney'}}` or
	- if using tailwind, add `fontFamily: {sans: ["Whitney", "Open Sans", ...defaultTheme.fontFamily.sans],title: ["Ginto", "Open Sans", ...defaultTheme.fontFamily.sans],},` under `theme.extend` object in `tailwind.config.js`.
