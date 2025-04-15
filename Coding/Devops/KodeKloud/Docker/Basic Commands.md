## __Container__

- `docker run nginx`
	- if the image is missing, pulls down the image
	- runs a container based off of the image
	- `docker run -d nginx` to detach, i.e. run in the background
		- `docker attach id_or_name_of_container`
	- `docker run -p 8080:80 nginx` 
		- `8080` (Host machine port) → `80` (Container port)
		- Now, you can access Nginx at `http://localhost:8080` from your **host machine**.
- `docker ps`
	- lists running containers
	- `docker ps -a` lists all containers
- `docker stop silly_sammet`
	- stops a container
	- `silly_sammet` is the name of the container. You can also use the id.
- `docker rm silly_sammet`
	- removes a container

| Command       | Purpose                                         | Container State                           | Example                                  |
| ------------- | ----------------------------------------------- | ----------------------------------------- | ---------------------------------------- |
| `docker run`  | Starts a **new container** from an image        | Container must **not** already be running | `docker run -it ubuntu /bin/bash`        |
| `docker exec` | Runs a command **inside an existing container** | Container must **already be running**     | `docker exec -it my_container /bin/bash` |
### Examples

- `docker run -d nginx` Start Nginx in detached mode
- `docker exec -it my_nginx /bin/bash` Attach a shell to it
## __Image__

- `docker images`
- `docker rmi nginx`
	- delete all related containers before you can run this command
- `docker pull nginx`
	- pulls down the image without running it