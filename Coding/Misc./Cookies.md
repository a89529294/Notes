# What are cookies?
- Bits of information(*key/value pairs*) that are stored in a user's browser when browsing a particular site.
- Once a cookie is set, a user's browser will send the cookie on every subsequent request to the site.
- *Cookies* allow HTTP to be **stateful**.

## What are signed cookies?
- Cookies by default are *unsigned*, meaning it can be *tampered* with by the *client* and the *server* would not know better.
- *Signed* cookies let the *server* know if a *signed* cookie has been *tampered* with. 
- For concreate examples see [[Coding/Node/Express/Cookies]]