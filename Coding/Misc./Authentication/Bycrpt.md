# bcrypt vs. bcryptjs
**bcrypt** can only run on *node*, whereas **bcryptjs** can run on *node* and *browser*.

## Demo Location
Demo is located at [colt steele bootcamp](https://github.com/a89529294/Colt_Steele_Web_Bootcamp) under the *Bcrypt* folder.

## Code Snippets
```js
const bcrypt = require("bcrypt");

const hashPassword = async (pw) => {
	const saltRounds = 10;
	const salt = await bcrypt.genSalt(saltRounds);

	/* You can pass in saltRounds or salt */
	const hashedPw = await bcrypt.hash(pw, saltRounds);
	/* const hashedPw = await bcrypt.hash(pw, salt); */

	await bcrypt.compare(pw, hashedPw).then((r) => console.log(r));
};

hashPassword("monkey");
```
Note that the *hashedPw* contains the *salt* so we don't have to save the *salt* ourselves. When `bycrpt` runs `compare(pw,hashedPw)` it automatically pulls out the *salt* and calls `hash(pw,salt)` and compares it to *hashedPw*.