__OAuth__ (Open Authorization) is about the process of a user authorizing an application to have a limited access to his data in a third-party application, like Google.

The main difference between __OAuth2__ and __OpenID Connect__ is that *OAuth2 is only concerned with authorization, while OpenID Connect is also concerned with authentication*. Authorization means granting access to resources, while authentication means verifying the identity of a user.

## Parties Involved
- Resource owner (you)
- Client (the website you are visiting)
- Resource server / Authorization Server (Google)

## Common Grant Types
- Authorization code flow (for server-side web app)
- Implicit Flow (for client-side web app)

## Prerequisites: register your app
Before we start, no matter which grant types we choose to implement, we have to __register our web applications in that third-party service__. It will return the credentials we need for the next step, such as client ID, client secret etc. Details can be found in third-party service, such as Google OAuth 2.0 API documentation.

### Authorization Code Flow
You are able to store client secret in your server to avoid exposing it to the public.

1. The client application initiates the authorization process by redirecting the user to the authorization server's authorization endpoint, typically through a browser or web view.
2. The user is presented with a login screen or a consent screen, where they authenticate themselves and approve the requested permissions or scopes.
3. Upon successful authentication and consent, the authorization server generates an *authorization code* and redirects the user back to the client application's specified redirect URI, along with the authorization code as a query parameter.
4. The client application receives the authorization code from the redirect URI.
5. The client application securely sends a request to the authorization server's token endpoint, including the authorization code, client credentials (client ID and client secret), redirect URI, and the grant type set to "authorization_code".
6. The authorization server verifies the authorization code, client credentials, and the redirect URI to ensure they match the previous authorization request.
7. If the validation is successful, the authorization server responds with an *access token*, a *refresh token* (optional), and other relevant information (such as token expiration time).
8. The client application can then use the access token to authenticate and access protected resources on behalf of the user by including it in the Authorization header of API requests.
9. If a refresh token was issued, the client application can use it to request a new access token when the current one expires, without requiring the user to re authenticate.

### Implicit Grant

1. The client application initiates the authorization process by redirecting the user to the authorization server's authorization endpoint, typically through a browser or web view.
2. The user is presented with a login screen or a consent screen, where they authenticate themselves and approve the requested permissions or scopes.
3. Upon successful authentication and consent, the authorization server generates an *access token* and includes it directly in the redirect URI fragment (#) of the response, along with other relevant information.
4. The authorization server redirects the user back to the client application's specified redirect URI, including the access token in the fragment part of the URL.
5. The client application receives the redirect from the authorization server and extracts the access token from the URL fragment.
6. The client application can then use the access token to authenticate and access protected resources on behalf of the user by including it in the Authorization header of API requests.
7. Since the access token is exposed in the URL fragment, the client application typically relies on JavaScript within the browser or web view to extract the access token from the URL and handle subsequent API requests.
8. The client application performs client-side validation and security checks on the received access token, such as verifying its expiration and integrity.
9. If the access token expires or the client application needs to request additional resources, it may need to redirect the user back to the authorization server for re authentication and consent.

### When to pick each grant
When to use __Implicit Grant__:

1. Client-side applications: The Implicit Grant is often used for client-side applications such as single-page web applications or mobile apps, where securely storing and exchanging an authorization code may be challenging or not feasible.
2. Simplicity: The Implicit Grant is simpler to implement since it doesn't involve the extra step of exchanging an authorization code for an access token. It reduces the complexity of the authentication flow.
3. Short-lived access: If the access token is short-lived and quickly expires, such as for low-risk or public API access, the Implicit Grant can be suitable. The client can request a new token by reinitiating the authorization process.

When to use __Authorization Code Grant__:
1. Server-side applications: The Authorization Code Grant is commonly used for server-side applications where the client secret can be securely stored, and the backend can handle the exchange of the authorization code for an access token.
2. Enhanced security: The Authorization Code Grant provides an extra layer of security by separating the authorization code from the access token. The authorization code is exchanged in a server-to-server communication, reducing the risk of exposing the access token.
3. Refresh tokens: If your application requires the ability to obtain a new access token without user involvement, the Authorization Code Grant with the inclusion of refresh tokens is preferred. Refresh tokens allow the client to obtain a new access token when the current one expires, without requiring the user to re authenticate.
4. Access to additional scopes: The Authorization Code Grant allows for a more fine-grained control of permissions by requesting specific scopes during the initial authorization request. This makes it suitable for scenarios where different scopes need to be requested for different API endpoints or resources.

## Flow Charts
![[authorization_code_flow.webp]]
![[implicit_code_flow.webp]]








