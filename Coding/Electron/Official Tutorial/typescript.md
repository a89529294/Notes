Electron's npm package also exports subpaths that contain a subset of Electron's TypeScript type definitions.

- `electron/main` includes types for all main process modules.
- `electron/renderer` includes types for all renderer process modules.
- `electron/common` includes types for modules that can run in main and renderer processes.

These aliases have no impact on runtime, but can be used for typechecking and autocomplete.

```js
const { app } = require('electron/main')  
const { shell } = require('electron/common')
```
