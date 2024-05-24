Applications that run within a Docker container use a _Dockerfile_ that contains the commands needed for creating the docker image and for launching the application. In applications that have multiple containers, a _Docker Compose_ file is used for managing all the containers at the same time.

## flow chart
1. create or pull an image
	1. `docker pull image`
	2. If you want to create your own image, you usually start with a `Dockerfile` that contains instructions for building the image. You then build the image using the `docker build` command. For example: `docker build -t my-app .`
2. launch a container: `docker run -d -p 80:80 nginx`

## Dockerfile
A _Dockerfile_ is a text file that contains the commands that are executed when creating a docker image. A docker image is a template that contains instructions for creating a runnable container.

## docker compose
Docker images are typically run with _Docker Compose_, which is a tool that helps running Docker applications with multiple containers.
In order to use Docker Compose, we need to create a [YAML](https://yaml.org/) file called `docker-compose.yml`. The file will contain information on all the containers that are run in the project.

Once we make sure we are in the right directory run
`docker compose up --build`


