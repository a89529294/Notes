## When does fetch() reject?
The returned *promise* only rejects when a network error is encountered.
  - there is no internet connection
  - wrong url
  - basically anytime the server fails to respond.
It *does not* reject on HTTP errors(404 etc)

```js
(async ()=>{
	const response = 
	await fetch('https://jsonplaceholder.typicode.com/post')

	/* or check response.status */
	if (!response.ok) throw new Error('unable to fetch!')
})()
```