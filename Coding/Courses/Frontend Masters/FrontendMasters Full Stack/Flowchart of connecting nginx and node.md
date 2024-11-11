1. `sudo vi /etc/nginx/sites-enabled/<domain-name>`
2. paste the following into above newly created file
```
server {
	listen 80 default_server;
	listen [::]:80 default_server;

	root /var/www/html;
	index index.html;

	server_name acdev.lol;

    location / {
		proxy_pass http://127.0.0.1:3000/;
	} 
}
```
3. `sudo vi /etc/nginx/nginx.conf`, find the `Virtual Host Configs` section and change `include /etc/nginx/sites-enabled/*` to `include /etc/nginx/sites-enabled/<domain-name>`
	1. Alternatively, just run `sudo ln -s /etc/nginx/sites-available/my_app /etc/nginx/sites-enabled/`
4. `sudo nginx -t` validate nginx configs
5. `sudo service nginx restart`
6. check your domain to see if its running, don't forget to run your node server!
7. if error, run `sudo tail -f /var/log/nginx/error.log`
8. for nginx status run `sudo systemctl status nginx`