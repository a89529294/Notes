1. ssh into remote server
2. https://certbot.eff.org/instructions pick your web server and os
3. follow instructions from above, certbot modifies our nginx config files, in this case `/etc/nginx/sites-enabled/fsfe` and `/etc/nginx/sites-enabled/blog.fsfe`(sub domain).
4. `sudo service nginx restart`
5. `sudo ufw allow https`