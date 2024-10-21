*It let us save and retrieve the browser's password manager.*
- **credentials** (email/password)
- **federated credentials** The **`FederatedCredential`** interface of the [Credential Management API](https://developer.mozilla.org/en-US/docs/Web/API/Credential_Management_API) provides information about credentials from a federated identity provider. A federated identity provider is an entity that a website trusts to correctly authenticate a user, and that provides an API for that purpose. (*Only available in chromium browsers*)
- public/private keys

*It let us implement auto login safely.*

## examples
```js
// dont forget to check if PasswordCredential exist, see below Pitfalls
const credentials = new PasswordCredential({
	id:"a@b.com",
	password:"pa$$word"
})

// save
await navigator.credentials.store(credentials)

// retrieve, used for auto login, see example in 
// /Users/admin/Desktop/frontend-masters/web-authentication/coffeemasters-authn/public/scripts/Auth.js
// init method
const credentials = navigator.credentials.get({
	password:true
})

// if you want to disable auto signin untill next time the user logs in manually, in logout method add
navigator.credentials.preventSilentAccess();
```

## Pitfalls
- Not all browsers support this api, *feature detection is important*.
```js
if ('PasswordCredential' in window) {...}
```
- *Sometimes auto login will not work* because of browser settings. On chrome, click on triple dots on the top right -> passwords and autofill -> google password manager to turn `Sign in automatically` on.