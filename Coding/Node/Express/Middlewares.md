- Express **middleswares** are functions that run during the request/response lifecycle.
- Each **middleware** has access to the *request* and *response* objects
- **Middleware** can end the request by sending back a response with methods like `res.send()`
- **Middlewares** can be chained together, one after another by calling `next()`

```js
app.use((req,res,next)=> // runs cb on every path every verb
	{                    // can also pass in a path to restrict when 
	...                  // the cb runs
	}
) 
app.get('/',(req,res,next)=>{...}) // runs cb on path '/' for GET requests

// The callbacks you pass in above are middlewares
```