```js
const express = require("express");
const session = require("express-session");
const app = express();

app.use(session({ secret: "thisisnotagoodsecret" }));

app.get("/viewcount", (req, res) => {
	req.session.count ? (req.session.count += 1) : (req.session.count = 1);
	res.send(`You have viewed this page ${req.session.count} times!`);
});

app.listen(3000, () => console.log("session demo listening on port 3000"));
```

- By using *express-session* the *server* automatically creates a *connect.sid* cookie and send it back the *client* if it does not alreay has one.
- The *session cookie* is used to associate a *client* and an *object* with the in-memory data store.
- `req.session` represents the *object* associated with the client. We can add and retrieve any properties we want.
- The reason a *secret* is needed is because we need to sign the *session cookie* to ensure it is not tampered with.
