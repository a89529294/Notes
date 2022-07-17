#### Requiring a file from another file
Lets say we want to access properties and functions from file B in file A. 
```js
//file A
const {fn1,prop1} = require('./fileB')
fn1();
console.log(prop1)
```
```js
//file B
module.exports = {
	fn1(){
		...
	},
	prop1:1
}
```
Keep in mind that whatever `module.exports` is holding will be exported.

#### Requiring a directory from another file
If you require a directory, node will look for the `index.js` file in that directory and import whatever is exported from that file.




