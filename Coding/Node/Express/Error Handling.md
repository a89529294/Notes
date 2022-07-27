1. There are two types of errors: *synchronous* and *asynchronous*.
2. Express comes with a built-in error handler that takes care of any errors that might be encountered in the app. This default error-handling middleware function is added at the end of the middleware function stack. [More info](https://expressjs.com/en/guide/error-handling.html)
3. Remember, *error handlers* are just middleware functions with two distinctions.
	1. They have four parameters `(err,req,res,next)` instead of the usual three `(req,res,next)`.
	2. They must be defined after other middlewars `app.use()` and `app.get()`, etc.
4. How you call `next()` with or without an *argument* determines what middleware get run next
```js
app.use((err,req,res,next)=>{
	next() // The next non error handler runs
})

app.use((err,req,res,next)=>{
	next(err) // The next error handler runs
})
```
5.  In Express, *404 responses* are not the result of an error, so the error-handler middleware will not capture them. This behavior is because a 404 response simply indicates the absence of additional work to do; in other words, Express has executed all middleware functions and routes, and found that none of them responded.
