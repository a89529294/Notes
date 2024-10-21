## loading environment variables

### directly in the command yo run your code
Defining the environment variables and their values *directly in the command to run your code*. 
`NODE_ENV=prod VIDEO_URL="https://www.youtube.com/watch?v=X2CYWg9-2N0" node index.js` (quotation needed only when value contains special chars)

### save into the current shell session
Save environment variables and their values to the *current shell session*.
`export NODE_ENV=prod VIDEO_URL="https://www.youtube.com/watch?v=X2CYWg9-2N0"`

### use dotenv
1. After installing the npm package, you can create a file called `.env` in the root of your project that will contain all of your environment variables in the format `NAME="VALUE"`.
2. Add the `.env` file into `.gitignore`.
3. As early as possible in your app, add `require("dotenv").config();`

## accessing environment variables
```js
if (process.env.NODE_ENV === "prod") {
    // do production-specific stuff
}

// don't want to ruin the surprise by hardcoding the URL!
// it might even change every few days!
redirectUserToSuperSecretVideo(process.env.VIDEO_URL);

```
