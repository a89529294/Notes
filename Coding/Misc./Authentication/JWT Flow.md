-   User credentials sent to `/signin`
-   `/signin` returns a JWT (signed with a key)
-   JWT is stored in `localStorage`
-   JWT is sent on every request (to API)
-   The server can read the JWT and extract user ID out of it

