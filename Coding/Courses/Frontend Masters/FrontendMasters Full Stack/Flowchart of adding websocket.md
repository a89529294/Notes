1. ssh into remote server
2. `sudo vi /etc/nginx/sites-enabled/<domain>`, modify the location block to include to more lines 
```
location / {
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_pass http://localhost:3000/;
}
```
3. `sudo nginx -t` then `sudo service nginx restart`
4. set up websocket in both html and server file, reference [link](https://github.com/a89529294/frontendMasters-full-stack/blob/main/index-ws.js) and [link](https://github.com/a89529294/frontendMasters-full-stack/blob/main/index.html)