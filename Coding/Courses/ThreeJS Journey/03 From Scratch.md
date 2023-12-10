- `npm init -y`
- `npm i three vite` 
- in `package.json` add 
```json
"scripts": {
	"dev": "vite",
	"build": "vite build"
}
```
- `npm run dev` to start local server
- in project root add `index.html` and `script.js`
- in `index.html` before end of body tag add `<script src="./script.js" type="module"></script>`
```js
// script.js
import * as THREE from "three";

console.log(THREE);
```

## reference
see `/Users/albert/Desktop/code/threejs-journey/03/exercise` for complete example.