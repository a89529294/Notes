# What are cookies?
- Bits of information(*key/value pairs*) that are stored in a user's browser when browsing a particular site.
- Once a cookie is set, a user's browser will send the cookie on every subsequent request to the site.
- *Cookies* allow HTTP to be **stateful**.

## What are signed cookies?
- Cookies by default are *unsigned*, meaning it can be *tampered* with by the *client* and the *server* would not know better.
- *Signed* cookies let the *server* know if a *signed* cookie has been *tampered* with. 
- For concrete examples see [[Coding/Node/Express/Cookies]]

## How to set up cookies?
Cookie can be set by:
- Server with `Set-cookie` header.
- Client side with `document.cookie`.

## Examples

```js
// expressjs
res.cookie('cookie1', 'value1', { httpOnly: true });
res.cookie('cookie2', 'value2', { maxAge: 3600000 });

// Set-Cookie: <name>=<value>; <attributes>
// value can be anything, just serialize it and encodeURIComponent it

// Set (browser side)
const data = { cookie1: "value1", cookie2: "value2" };
document.cookie = `data=${encodeURIComponent(JSON.stringify(data))}; Path=/`;

// Read
const cookieData = JSON.parse(decodeURIComponent(cookieValue));
```

