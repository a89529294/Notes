1. ssh into remove server 
2. `sudo vi /etc/nginx/sites-enabled/fsfe`
3. find `listen [::]:443` and `listen 443` add `http2` after each. so it becomes `listen [::]:443 http2` and `listen 442 http2`
4. `sudo service nginx restart`