## commonjs
```js
__dirname  // The current module's directory name
__filename // The current module's file name
```

## es module pre node v20.11.0
```js
import * as url from 'url'; 
const __dirname = url.fileURLToPath(new URL('.', import.meta.url)); 
const __filename = url.fileURLToPath(import.meta.url);
```

## es module node >= v20.11.0
```js
import.meta.dirname  // The current module's directory name
import.meta.filename // The current module's file name
```