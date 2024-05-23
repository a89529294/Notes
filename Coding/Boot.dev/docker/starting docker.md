`docker run -d -p 80:80 docker/getting-started`

### `-d` (detached mode)
The `-d` flag stands for "detached mode." When you run a container in detached mode, it runs in the background, and you get back to your command prompt immediately. You can still manage and interact with the container using Docker commands, but the container's output will not be displayed in your terminal.

### `-p` (publish)
The `-p` flag is used to publish a container's port to the host. It allows you to map a port on your local machine (host) to a port inside the container. The syntax is `-p host_port:container_port`.

### docker/getting-started
is the name of the image
