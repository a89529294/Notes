## Unsigned cookies
```js
const cookieParser = require("cookie-parser");

app.use(cookieParser());

app.get('/showcookies',(req,res)=>{
	res.send(req.cookies); /* {fruit:grape} */
})

app.get('/setcookies',(req,res)=>{
	res.cookie('fruit','grape');
	res.send('Your cookies have been set.');
})
```

## Signed cookies
```js
const cookieParser = require("cookie-parser");

app.use(cookieParser("thisismysecret"));

app.get('/showcookies',(req,res)=>{
	res.send(req.signedCookies); /* {secret:topsecret} */
})

app.get('/setcookies',(req,res)=>{
	res.cookie('secret','topsecret',{signed:true});
	res.send('Your cookies have been set.');
})
```

The *difference* is if **signed cookies** are tampered with the value `req.signedCookies` will become `{}` or `{key:false}`