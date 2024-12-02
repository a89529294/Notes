1. `sudo chown -R $USER:$USER /var/www`
2. `mkdir /var/www/app`
3. `cd /var/www/app`
4. `git init`
5. `touch app.js`
6. `npm init -y`
7. create a new basic server 
```js
const http = require('http');

http.createServer(function(req,res){
	res.write('hello world');
	res.end();
}).listen(3000)
```