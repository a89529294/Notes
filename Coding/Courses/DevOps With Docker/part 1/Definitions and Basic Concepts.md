_devops_ means the release, configuring, and monitoring of software is in the hands of the very people who develop it.

_Docker_ is a set of tools to deliver software in containers.
_Containers_ are packages of software that include the application and its dependencies.

## Images and Containers

Containers are _instances_ of images.

Think of a _container as a ready-to-eat meal_ that you can simply heat up and consume. An _image is the recipe or ingredients_ for that meal.

In short, an _image is like a blueprint_ or template, while a _container is an instance of that blueprint_ or template.

### Images

A Docker image is a file. An image never changes; you can not edit an existing file. Creating a new image happens by starting from a base image and adding new **layers** to it. We will talk about layers later, but you should think of _images as immutable_, they can not be changed after they are created.

If images are used to create containers, where do images come from? This image file is built from an instructional file named **Dockerfile** that is parsed when you run `docker image build`.

Dockerfile is a file that is by default called _Dockerfile_, that looks something like this
```docker
FROM <image>:<tag>

RUN <install some dependencies>

CMD <command that is executed on `docker container run`>
```

If we go back to the cooking metaphor, as Dockerfile provides the instructions needed to build an image you can think of that as the recipe for images. We're now 2 recipes deep, as _Dockerfile is the recipe for an image and an image is the recipe for a container._ The only difference is that Dockerfile is written by us, whereas image is written by our machine based on the Dockerfile!

### Containers

Containers only contain what is required to execute an application; and you can start, stop and interact with them. They are **isolated** environments in the host machine with the ability to interact with each other and the host machine itself via defined methods (TCP/UDP).

## Docker CLI Basics

"Docker Engine" is made up of 3 parts: CLI, a REST API and Docker daemon.

When you run a command, e.g. `docker run <name_of_image>`, behind the scenes the client sends a request through the REST API to the **Docker daemon** which takes care of images, containers and other resources.
## commands

### container management
```bash
# List containers
docker container ls                    # List running containers
docker container ls -a                 # List all containers (including stopped)
docker container ls -q                 # List only container IDs
docker container ls --format "{{.ID}}: {{.Names}}"  # Custom format output

# Remove containers
docker container rm CONTAINER_ID       # Remove stopped container
docker container rm -f CONTAINER_ID    # Force remove running container
docker container prune                 # Remove all stopped containers

# Create and start a container
docker container run [OPTIONS] IMAGE [COMMAND]
docker container run -d -p 80:80 --name mywebserver nginx
docker container run --restart always IMAGE  # Auto restart policy

# Execute command in running container
docker container exec [OPTIONS] CONTAINER COMMAND
docker container exec -it mycontainer bash
docker container exec -u root mycontainer bash  # Run as root

# View container details
docker container logs -f -t CONTAINER_NAME
docker container inspect CONTAINER_NAME
docker container stats                 # Show live resource usage
docker container top CONTAINER_NAME    # Show running processes

# Start/Stop/Pause containers
docker container start CONTAINER_NAME_OR_ID
docker container stop CONTAINER_NAME_OR_ID
docker container restart CONTAINER_NAME_OR_ID
docker container pause CONTAINER_NAME_OR_ID
docker container unpause CONTAINER_NAME_OR_ID
```

### image management
```bash
# List images
docker image ls                        # List all images
docker image ls -a                     # Include intermediate images
docker image ls -q                     # Only show image IDs
docker image ls --format "{{.Repository}}:{{.Tag}}"

# Remove images
docker image rm IMAGE_ID               # Remove specific image
docker image rm -f IMAGE_ID           # Force remove image
docker image prune                     # Remove unused images
docker image prune -a                  # Remove all unused images

# Build and manage images
docker image build -t myapp:1.0 .
docker image build --no-cache .        # Build without using cache
docker image tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]
docker image push registry.example.com/myapp:1.0
docker image pull nginx:latest
docker image history IMAGE_NAME        # Show image layers
docker image inspect IMAGE_NAME        # Show detailed image info
```

### volume management
```bash
# List and manage volumes
docker volume ls
docker volume create mydata
docker volume rm VOLUME_NAME
docker volume prune                    # Remove all unused volumes
docker volume inspect VOLUME_NAME

# Run container with volumes
docker container run -v mydata:/app/data IMAGE
docker container run -v $(pwd):/app IMAGE  # Bind mount current directory
```

### network management
```bash
# List and manage networks
docker network ls
docker network create --driver bridge mynetwork
docker network rm NETWORK_NAME
docker network prune                   # Remove all unused networks
docker network inspect NETWORK_NAME

# Container networking
docker network connect mynetwork CONTAINER_NAME
docker network disconnect mynetwork CONTAINER_NAME
```

### system commands
```bash
# System information
docker system df                       # Show docker disk usage
docker system df -v                    # Verbose disk usage
docker system info                     # System-wide information
docker system events                   # Real-time events

# Cleanup commands
docker system prune                    # Remove unused data
docker system prune -a --volumes       # Remove all unused objects
```

### common command options
```bash
-d, --detach                          # Run in background
-p, --publish HOST:CONTAINER          # Publish ports
-v, --volume SOURCE:TARGET            # Mount volume
-e, --env KEY=VALUE                   # Set environment variables
--name STRING                         # Assign container name
--network STRING                      # Connect to network
--restart always|unless-stopped|on-failure # Restart policy
--memory LIMIT                        # Memory limit
--cpus LIMIT                          # CPU limit
-it                                   # Interactive terminal
--rm                                  # Remove container when it exits
```