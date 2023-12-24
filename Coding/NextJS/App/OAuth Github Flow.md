1. Go to `https://github.com/settings/developers` and set up a new OAuth app.
2. _User_ clicks on sign up
3. Browser redirect _user's browser_ to `github.com/login/oauth/authorize?client_id=123`. `client_id` is defined in `.env.local` `GITHUB_CLIENT_ID`.
4. _Github_ asks _user_ if they are okay with sharing information with our app.  If they are, _user's browser_ get redirected to `http://localhost:3000/api/auth/callback/github?code=456` . This url is found under `https://github.com/settings/applications/${app_slug}` .
5. _Our server_ takes the __code__ and makes a followup POST request to _Github_, `github.com/login/oauth/access_token {clientId, clientSecret, code}`.
6. _Github_ makes sure clientId, clientSecret and code are valid then responds with an _access_token=abc123_.  (TODO check how access_token is sent, is it in a POST request or GET)
7. _Our server_ makes a request to _Github_ with the access_token to get the details about the user. `api.github.com/user Authorization: Bearer abc123`
8. After verification _Github_ responds with the user's profile `{name,email,avatar}`.
9. _Our server_ creates a new user in our database.
10. _Our server_ sends a cookie to the _user's browser_. That cookie tells us who is making a request to _our server_. 