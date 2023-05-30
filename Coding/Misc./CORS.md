## Same Origin Policy
A default *security measure in browsers* that restricts how scripts from one origin interact with resources from another origin (cross-origin).

We consider *two URLs to be of the same origin* if they have the same _scheme_, _domain_, and _port number_.

Browsers implementing the Same Origin Policy *restrict website scripts served on one origin* from making requests to another origin using methods such as _[XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest)_ or the [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API).

## Cross Origin Resource Sharing
To address the need for accessing third party APIs, **the CORS policy determines how scripts served by one origin can request resources on another origin.** The CORS policy defines specific HTTP headers that need to be included in the request/response interaction; allowing the server to communicate which origins it will allow requests from. The browser then enforces this by allowing or preventing scripts from accessing the response.

## Summary
- If the request *DOES NOT include a origin*, then it will be considered a *same origin request*, the browser will always allow it. This happens when you paste a url *directly into the url bar* or using _curl_.
- If a request *DOES include a origin*, which happens automatically when *fetch/xhr* runs on a domain A requesting api from domain B, there are possible two outcomes:
	- [Simple Requests](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS#simple_requests): no preflight happens, if the response includes `access-control-allow-origin` that includes the origin, the browser will allow the request handler to access the data.
	- Non-Simple Requests: Any request that is *not a simple request is a non-simple request*. The browser treats these kinds of requests a little differently. *Before sending the actual request, the browser will send what we call a preflight request*, to check with the server if it allows this type of request.

## Misc
- By default, the *CORS policy doesn’t allow including credentials in a cross-origin request* unless both the request includes a flag to include credentials and the server responds with the _access-control-allow-credentials_ set to true.
- *Credentials* can be cookies, authorization headers, or TLS client certificates.
```js
fetch("https://example.com", {
  credentials: "include",
});
```