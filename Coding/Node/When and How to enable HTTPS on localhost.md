## When to use HTTPS on localhost
When developing locally, use `http://localhost` by default. *Service Workers, Web Authentication API, and more will work*. However, in the following cases, you'll need HTTPS for local development:
- Setting Secure cookies in a consistent way across browsers
- Debugging mixed-content issues
- Using HTTP/2 and later
- Using third-party libraries or APIs that require HTTPS
- Using a custom hostname
Refer to [when-to-use-local-https](https://web.dev/articles/when-to-use-local-https)for details.

## How to use HTTPS on localhost
1. `brew install mkcert` only run this if you haven't before on the device.
2. `mkcert -install`
3. In project root directory `mkcert localhost`
4. Follow below snippet
```js 
import https from "https";
import fs from "fs";
import express from "express";
import * as url from "url";

const __dirname = url.fileURLToPath(new URL(".", import.meta.url));
const options = {
	key: fs.readFileSync(__dirname + "localhost-key.pem"),
	cert: fs.readFileSync(__dirname + "localhost.pem"),
};

const app = express();
var httpsServer = https.createServer(options, app);
httpsServer.listen(port);
```