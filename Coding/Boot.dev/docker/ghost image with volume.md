1. `docker volume create ghost-vol`
2. `docker pull ghost`
3. `docker run -d -e NODE_ENV=development -e url=http://localhost:3001 -p 3001:2368 -v ghost-vol:/var/lib/ghost/content ghost

In step 3 we bound `ghost-vol` to `/var/lib/ghost/content` in the container

4. `docker ps` then copy the running ghost container's id 
5. `docker restart CONTAINER_ID` 

We should still see the changes we made in the previous start of the container

Note - When you run a container with `docker run`, Docker creates a container instance with specific settings, including environment variables, port mappings, and volume mounts.
- Docker stores the configuration and metadata for this container instance in its internal storage (usually located in `/var/lib/docker` on Linux systems).

_If we were to create a new container off of the same image, we will need to re bind the volume to the new container_