Follow the instructions in [[Flowchart of connecting nginx and node]] except for the config file, use the following instead
```txt
server {
    listen 80;
    listen [::]:80;
    server_name acdev.lol www.acdev.lol;

    root /var/www/react_app;  # Path to your built React app
    
    location / {
        try_files $uri $uri/ /index.html;
    }

}
```