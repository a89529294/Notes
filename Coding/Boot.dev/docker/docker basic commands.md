`docker --help`
`docker ps`: lists all _running_ docker containers
`docker ps -a`: lists all docker containers
`docker stats`: similar to above
`docker stop CONTAINER_ID`
`docker stop $(docker ps -q)` stops all running containers
`docker kill CONTAINER_ID`
`docker exec CONTAINER_ID ls`
`docker exec -it CONTAINER_ID /bin/sh` allows us to just run `ls` 
`exit` to exit from above