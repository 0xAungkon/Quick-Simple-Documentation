## **Basic Docker Commands**

- `**docker --version**`: Check Docker version.
- `**docker info**`: Display system-wide information.
- `**docker --help**`: Get help and list commands.
- `**docker run IMAGE**`: Run a container from an image.
- `**docker pull IMAGE**`: Download an image from a registry.
- `**docker images**`: List all available images.
- `**docker ps**`: List running containers.
- `**docker ps -a**`: List all containers (including stopped ones).
- `**docker stop CONTAINER**`: Stop a running container.
- `**docker start CONTAINER**`: Start a stopped container.
- `**docker restart CONTAINER**`: Restart a container.
- `**docker pause CONTAINER**`: Pause a running container.
- `**docker unpause CONTAINER**`: Unpause a paused container.
- `**docker rm CONTAINER**`: Remove a stopped container.
- `**docker rmi IMAGE**`: Remove an image.
- `**docker search TERM**`: Search for images on Docker Hub.
- `**docker logs CONTAINER**`: View container logs.
- `**docker exec -it CONTAINER COMMAND**`: Run a command in a running container.
- `**docker build -t IMAGE:TAG PATH**`: Build a Docker image from a Dockerfile.
- `**docker push IMAGE:TAG**`: Push an image to a registry.
- `**docker commit CONTAINER NEW_IMAGE**`: Create a new image from a container.
- `**docker network ls**`: List Docker networks.
- `**docker volume ls**`: List Docker volumes.
- `**docker version**`: Show Docker version information.
- `**docker login**`: Log in to a Docker registry.
- `**docker logout**`: Log out from a Docker registry.

## **Container Lifecycle Management**

- `**docker run -d IMAGE**`: Run a container in detached mode.
- `**docker run -p HOST_PORT:CONTAINER_PORT IMAGE**`: Map ports.
- `**docker run -v HOST_DIR:CONTAINER_DIR IMAGE**`: Mount volumes.
- `**docker stats**`: Show container resource usage statistics.
- `**docker top CONTAINER**`: Display running processes in a container.
- `**docker inspect CONTAINER/IMAGE**`: View detailed information.
- `**docker events**`: Monitor Docker events.
- `**docker rename OLD_NAME NEW_NAME**`: Rename a container.
- `**docker cp CONTAINER:SRC_PATH DEST_PATH**`: Copy files between a container and the local filesystem.
- `**docker wait CONTAINER**`: Block until a container stops, then print its exit code.
- `**docker kill CONTAINER**`: Send a SIGKILL to a container.
- `**docker attach CONTAINER**`: Attach to a running container's STDIN, STDOUT, and STDERR.
- `**docker export CONTAINER > OUTPUT_FILE**`: Export a container's filesystem as a tarball.
- `**docker import INPUT_FILE**`: Import an exported container filesystem as an image.

## **Docker Compose**

- `**docker-compose up**`: Start services defined in a `**docker-compose.yml**` file.
- `**docker-compose down**`: Stop and remove containers defined in a `**docker-compose.yml**` file.
- `**docker-compose ps**`: List containers managed by Docker Compose.
- `**docker-compose logs**`: View logs for services managed by Docker Compose.
- `**docker-compose build**`: Build or rebuild services.
- `**docker-compose config**`: Validate and view the merged Compose file.
- `**docker-compose pull**`: Pull service images.
- `**docker-compose push**`: Push service images.
- `**docker-compose restart**`: Restart services.
- `**docker-compose scale**`: Set number of containers for a service.

## **Docker System Management**

- `**docker system df**`: Show disk usage.
- `**docker system prune**`: Remove all stopped containers, dangling images, and unused networks and volumes.
- `**docker system prune -a**`: Remove all unused containers, images, networks, and volumes.
- `**docker history IMAGE**`: View image history.
- `**docker inspect --format="{{.NetworkSettings.IPAddress}}" CONTAINER**`: Get a container's IP address.

## **Advanced Docker Commands**

- `**docker save -o OUTPUT_FILE IMAGE**`: Save an image to a tarball.
- `**docker load -i INPUT_FILE**`: Load an image from a tarball.
- `**docker diff CONTAINER**`: Inspect changes to files or directories on a container's filesystem.
- `**docker update**`: Update configuration of one or more containers.
- `**docker volume create VOLUME**`: Create a named volume.
- `**docker volume inspect VOLUME**`: Inspect a volume.
- `**docker network create NETWORK**`: Create a custom network.
- `**docker network inspect NETWORK**`: Inspect a network.
- `**docker network connect NETWORK CONTAINER**`: Connect a container to a network.
- `**docker network disconnect NETWORK CONTAINER**`: Disconnect a container from a network.
- `**docker tag SOURCE_IMAGE:TAG TARGET_IMAGE:TAG**`: Tag an image.
- `**docker push REGISTRY/IMAGE:TAG**`: Push an image to a custom registry.
- `**docker pull REGISTRY/IMAGE:TAG**`: Pull an image from a custom registry.
- `**docker login REGISTRY**`: Log in to a custom registry.
- `**docker plugin install PLUGIN**`: Install a Docker plugin.
- `**docker plugin ls**`: List installed Docker plugins.
- `**docker plugin disable PLUGIN**`: Disable a Docker plugin.
- `**docker plugin enable PLUGIN**`: Enable a Docker plugin.
- `**docker plugin upgrade PLUGIN**`: Upgrade a Docker plugin.
- `**docker plugin remove PLUGIN**`: Remove a Docker plugin.

## **Docker Swarm**

- `**docker swarm init**`: Initialize a swarm.
- `**docker swarm join**`: Join a swarm as a worker or manager.
- `**docker swarm leave**`: Leave a swarm.
- `**docker swarm update**`: Update a swarm.
- `**docker service create**`: Create a new service.
- `**docker service scale**`: Scale a service up or down.
- `**docker service inspect**`: Inspect a service.
- `**docker service ps**`: List the tasks of a service.
- `**docker service logs**`: Fetch the logs of a service.
- `**docker stack deploy**`: Deploy a new stack or update an existing stack.
- `**docker stack ls**`: List stacks.
- `**docker stack rm**`: Remove one or more stacks.
- `**docker stack services**`: List services in a stack.
- `**docker stack ps**`: List tasks in a stack.
- `**docker secret create**`: Create a secret.
- `**docker secret ls**`: List secrets.

## **Docker Advanced Network**

- `**docker network create --driver overlay NETWORK**`: Create an overlay network for Docker swarm.
- `**docker network create --driver macvlan NETWORK**`: Create a MACVLAN network.
- `**docker network create --driver bridge NETWORK**`: Create a bridge network.
- `**docker network create --driver host NETWORK**`: Create a host network.
- `**docker network inspect --format '{{json .Containers}}' NETWORK**`: List containers connected to a network.

## **Miscellaneous Commands**

- `**docker system events**`: Stream real-time events from the server.
- `**docker system df -v**`: Show detailed disk space usage.
- `**docker pause $(docker ps -q)**`: Pause all running containers.
- `**docker unpause $(docker ps -q)**`: Unpause all paused containers.
- `**docker logs --tail N CONTAINER**`: Show the last N lines of a container's logs.
- `**docker ps -q -f status=exited**`: List only container IDs of exited containers.
- `**docker build --build-arg KEY=VALUE -t IMAGE:TAG PATH**`: Pass build arguments to a Dockerfile.
- `**docker run -e KEY=VALUE IMAGE**`: Set environment variables.
- `**docker run --rm IMAGE**`: Automatically remove the container when it exits.
- `**docker exec -u USER CONTAINER COMMAND**`: Run a command as a specific user in a container.
- `**docker attach CONTAINER**`: Attach to a running container's STDIN, STDOUT, and STDERR.
