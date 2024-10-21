`/etc/nginx/sites-enabled/<domain>` 
```
server {
        listen 80 default_server;
        listen [::]:80 default_server;

        root /var/www/html;
		index index**.html;

        server_name acdev.lol;

        # Serve static files from Vite build output directory

        location / {
                root /var/www/app/simple-react-app/dist; # Path to your Vite build output directory
                index index**.html;
        }

        error_page 404 = @myownredirect;

        location @myownredirect {
                return 302 /;
        }

        location /api/ {
              proxy_pass http://127.0.0.1:3000/api/;
        }

}
```

## notes
- build locally then upload using `scp path-to-file albert@<ip>:path-to-file-on-server`
- might need to restart `pm2`
	- `pm2 list` find name of app
	- `pm2 stop <name-of-app>`
	- `pm2 start app.js --watch`
	- `pm2 save` then `pm2 startup`