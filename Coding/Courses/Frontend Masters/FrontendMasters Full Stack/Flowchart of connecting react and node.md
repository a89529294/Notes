1. Modify `/etc/nginx/sites-available/mydomain.com` 
```txt
// paste this right after 
// root /var/www/react_app;  # Path to your built React app
  
  location /api {
        proxy_pass http://127.0.0.1:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    }
```
2. `sudo nginx -t` validate nginx configs
3. `sudo service nginx restart` or `sudo nginx -s reload`