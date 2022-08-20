The difference between path matching when it comes to `app.use()` and the standard `app.METHOD()` is that `app.use()` matches on base path and `app.METHOD()` matches on exact path.
```js
app.use('/',(req,res)=>{...}) // matches every incoming request regardless of verb	

app.get('/',(req,res)=>{...}) // matches only '/' for GET requests

app.all('/',(req,res)=>{...}) // matches only '/' for all requests regardless of verb
```