A route that responds to GET requests to the root path of the application is created as follows.
```javascript
import { Hono } from "https://deno.land/x/hono@v3.7.4/mod.ts";

const app = new Hono();

app.get("/", (c) => c.text("Hello World!"));

Deno.serve(app.fetch);
```

_Query parameters_ are available through the `query` method of the `req` attribute of the context object `c`.

```javascript
import { Hono } from "https://deno.land/x/hono@v3.7.4/mod.ts";

const app = new Hono();

app.get("/", (c) => c.text(`Name: ${c.req.query("name")}`));

Deno.serve(app.fetch);
```

_Path parameters_ are available through the `param` method of the `req` attribute of the context object `c`.

```javascript
import { Hono } from "https://deno.land/x/hono@v3.7.4/mod.ts";

const app = new Hono();

app.get("/:id", (c) => c.text(`Id: ${c.req.param("id")}`));

Deno.serve(app.fetch);
```
