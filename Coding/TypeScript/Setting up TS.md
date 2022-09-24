## No Transpilers (babel)
1. `npm i typescript --save-dev` in root of project
2. `npx tsc path_to_file` to convert *TS* to *JS*

## With Babel
1. `npm i typescript @babel/core @babel/cli --save-dev` in root of project
2. `"build": "babel src -d lib"` add this to *scripts* in *package.json*
3. `npm run build` will transpile all the files in *src* and put them in *lib*. Right now *Babel* will just copy files over with no modification.
4. You need to enable some *presets* for *Babel* to know how to transpile your code.
5. `npm install @babel/preset-env @babel/preset-typescript --save-dev` in root of project
6. `touch babel.config.json` in root of project then add `{ "presets": ["@babel/preset-env","@babel/preset-typescript"] }` in it.
7. `npm run build` again and you will see the files in *src* are modified.
8. By default *Babel* will only transpile *JS* files so you need to edit *script:build* to `"build":"babel src -d lib --extensions '.ts,.js'"` to also handle *TS* files. 
