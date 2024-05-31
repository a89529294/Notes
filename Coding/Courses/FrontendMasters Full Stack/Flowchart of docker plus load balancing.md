1. ssh into remote server
2. `sudo apt install docker.io`
3. create a `Dockerfile` in project root
4. make sure you are in project root `sudo docker build -t <image-name> .`
5. `sudo docker run -d -p 3000:3000 <image-name>`
6. `sudo docker run -d -p 3001:3000 <image-name>`
7. edit `/etc/nginx/nginx.conf` add the following inside http block
```
 upstream nodebackend {
                server localhost:3000;
                server localhost:3001;
        }
```
8. edit `/etc/nginx/sites-enabled/fsfe` modify `proxy_pass http://localhost:3000;` to `proxy_pass http://nodebackend;`
9. `sudo nginx -t`, `sudo service nginx restart`