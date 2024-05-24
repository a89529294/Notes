```yml
services:
	api:
		build: api
		restart: unless-stopped
		volumes:
			- ./api:/app
		ports:
			- 8000:8000
		depends_on:
			- database
	database:
		container_name: postgresql_database
		image: postgres:16.1
		restart: unless-stopped
		env_file:
			- project.env
```

1. **services**:
    - This defines the services that will be part of your application. In this case, you have one service called `api`.
2. **api**:
    - This is the name of the service. It can be anything you choose.
3. **build: api**:
    - This specifies that Docker should build an image for the `api` service using the Dockerfile located in the `api` directory on the host machine.
4. **restart: unless-stopped**:
    - This tells Docker to automatically restart the container if it stops, unless it is explicitly stopped by the user.
5. **volumes**:
    - This section defines the volume mappings. The syntax is `host_path:container_path`.
    - `./api:/app`:
        - This maps the `./api` directory on the host machine to the `/app` directory inside the container.
        - Any changes made to the files in `./api` on the host machine will be immediately reflected inside the container in `/app`, and vice versa.
        - This is useful for development environments because it allows you to edit files on your host machine using your preferred text editor or IDE, and see the changes take effect in the running container without needing to rebuild the image or restart the container.
6. **ports**:
    - This section maps the host machine's port to the container's port.
    - `8000:8000`:
        - This maps port 8000 on the host machine to port 8000 in the container.
        - This means that if you access `http://localhost:8000` on your host machine, the request will be forwarded to port 8000 on the container.
7. **depends_on**: 
	1. only guarantees the start up order, does not guarente the readiness 