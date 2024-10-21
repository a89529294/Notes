1. download the font and put it in the public folder
2. in `index.css` add the following under `@layer base`
```css
@font-face {
font-family: "Jost";
font-style: normal;
font-display: swap;
src: url(/jost-variable.ttf) format("ttf");
} 
/* no need to specify font weight since this is a variably font */
```
3. in `tailwind.config.js` add the following inside `theme.extend`, also import `const defaultTheme = require("tailwindcss/defaultTheme");`
```js
fontFamily: {
sans: ["Jost", ...defaultTheme.fontFamily.sans],
},
```
4. now the whole site uses `Jost` by default