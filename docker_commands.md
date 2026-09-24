# Docker Commands Documentation

## 1. Introduction to Docker

Docker is a platform used to **create, run, and manage applications inside containers**.

A container is a lightweight environment that contains everything an application needs to run, such as:

* Application code
* Libraries
* Dependencies
* Configuration
* Runtime environment

Docker helps developers run applications consistently on different systems.

---

# 2. Basic Docker Concepts

Before using Docker commands, it is useful to understand these basic terms.

| Term       | Meaning                                        |
| ---------- | ---------------------------------------------- |
| Docker     | Platform for creating and running containers   |
| Image      | A template used to create containers           |
| Container  | A running instance of an image                 |
| Dockerfile | File containing instructions to build an image |
| Docker Hub | Online registry for Docker images              |
| Volume     | Used for persistent data storage               |
| Network    | Allows containers to communicate               |
| Repository | Collection of Docker images                    |

---

# 3. Check Docker Installation

## Check Docker Version

```bash
docker --version
```

Example:

```text
Docker version 28.x.x
```

This command displays the installed Docker version.

---

## Display Docker Information

```bash
docker info
```

This displays detailed information about the Docker installation.

It can show:

* Number of containers
* Number of images
* Docker storage driver
* Docker version
* Running containers
* Docker root directory

---

# 4. Docker Help Commands

## Display General Help

```bash
docker --help
```

Shows the available Docker commands.

---

## Get Help for a Specific Command

```bash
docker <command> --help
```

Example:

```bash
docker run --help
```

This displays options available for the `docker run` command.

---

# 5. Docker Images

Docker images are templates used to create containers.

## List Docker Images

```bash
docker images
```

or

```bash
docker image ls
```

Example output:

```text
REPOSITORY    TAG       IMAGE ID       CREATED        SIZE
ubuntu        latest    abc123456      2 weeks ago    78MB
nginx         latest    xyz987654      1 week ago     188MB
```

---

## Download an Image

```bash
docker pull <image-name>
```

Example:

```bash
docker pull ubuntu
```

This downloads the Ubuntu image from Docker Hub.

---

## Download a Specific Version

```bash
docker pull ubuntu:22.04
```

Here:

* `ubuntu` = image name
* `22.04` = image tag/version

---

## Remove an Image

```bash
docker rmi <image-name>
```

Example:

```bash
docker rmi ubuntu
```

You can also use the image ID:

```bash
docker rmi <image-id>
```

---

## Remove Multiple Images

```bash
docker rmi image1 image2 image3
```

Example:

```bash
docker rmi ubuntu nginx redis
```

---

## Inspect an Image

```bash
docker image inspect <image-name>
```

Example:

```bash
docker image inspect ubuntu
```

This displays detailed information about the image.

---

# 6. Docker Containers

A container is a running or stopped instance of a Docker image.

## Create and Run a Container

```bash
docker run <image-name>
```

Example:

```bash
docker run ubuntu
```

---

## Run a Container Interactively

```bash
docker run -it ubuntu
```

Here:

* `-i` = Interactive mode
* `-t` = Allocate a terminal

Example:

```bash
docker run -it ubuntu
```

You can now use the Ubuntu terminal inside the container.

---

## Run Container in Background

```bash
docker run -d <image-name>
```

Example:

```bash
docker run -d nginx
```

Here:

* `-d` = Detached mode

The container runs in the background.

---

## Give a Container a Name

```bash
docker run --name <container-name> <image-name>
```

Example:

```bash
docker run --name myubuntu ubuntu
```

Now the container is named `myubuntu`.

---

## Run Container with a Name in Interactive Mode

```bash
docker run -it --name myubuntu ubuntu
```

---

# 7. List Containers

## Show Running Containers

```bash
docker ps
```

This shows only currently running containers.

---

## Show All Containers

```bash
docker ps -a
```

This shows:

* Running containers
* Stopped containers
* Exited containers

---

## Show Only Container IDs

```bash
docker ps -q
```

---

## Show All Container IDs

```bash
docker ps -aq
```

---

# 8. Start and Stop Containers

## Start a Stopped Container

```bash
docker start <container-name>
```

Example:

```bash
docker start myubuntu
```

---

## Stop a Running Container

```bash
docker stop <container-name>
```

Example:

```bash
docker stop myubuntu
```

---

## Restart a Container

```bash
docker restart <container-name>
```

Example:

```bash
docker restart myubuntu
```

---

# 9. Remove Containers

## Remove a Container

```bash
docker rm <container-name>
```

Example:

```bash
docker rm myubuntu
```

The container must normally be stopped before removing it.

---

## Force Remove a Container

```bash
docker rm -f <container-name>
```

Example:

```bash
docker rm -f myubuntu
```

This stops and removes the container.

---

## Remove All Stopped Containers

```bash
docker container prune
```

Docker will ask for confirmation before removing stopped containers.

---

# 10. Execute Commands Inside a Container

## Execute a Command

```bash
docker exec <container-name> <command>
```

Example:

```bash
docker exec myubuntu ls
```

This runs the `ls` command inside the container.

---

## Open a Shell Inside a Running Container

```bash
docker exec -it <container-name> bash
```

Example:

```bash
docker exec -it myubuntu bash
```

If Bash is not available, you can use:

```bash
docker exec -it myubuntu sh
```

---

# 11. View Container Logs

## Display Container Logs

```bash
docker logs <container-name>
```

Example:

```bash
docker logs myubuntu
```

This displays the output generated by the container.

---

## Follow Logs in Real Time

```bash
docker logs -f <container-name>
```

Here:

* `-f` = Follow

Example:

```bash
docker logs -f mycontainer
```

Press `Ctrl + C` to stop viewing the logs.

---

# 12. Inspect Containers

## Inspect a Container

```bash
docker inspect <container-name>
```

Example:

```bash
docker inspect myubuntu
```

This displays detailed information about:

* Container ID
* Network
* IP address
* Mounts
* Configuration
* Environment variables
* Status

---

# 13. View Container Resource Usage

```bash
docker stats
```

This displays live resource usage.

It can show:

* CPU usage
* Memory usage
* Network usage
* Block I/O
* Process information

---

## Check a Specific Container

```bash
docker stats <container-name>
```

Example:

```bash
docker stats mycontainer
```

---

# 14. Port Mapping

Containers can expose applications through ports.

## Map a Host Port to a Container Port

```bash
docker run -p <host-port>:<container-port> <image>
```

Example:

```bash
docker run -p 8080:80 nginx
```

Here:

* `8080` = Port on your computer
* `80` = Port inside the container

You can access the application through:

```text
http://localhost:8080
```

---

# 15. Run Container in Background with Port Mapping

```bash
docker run -d -p 8080:80 nginx
```

This runs Nginx in the background and maps port `8080` on the host to port `80` in the container.

---

# 16. Environment Variables

Environment variables can be passed to containers using `-e`.

```bash
docker run -e VARIABLE=value <image>
```

Example:

```bash
docker run -e APP_ENV=development myapp
```

Multiple variables can be added:

```bash
docker run -e USER=admin -e PASSWORD=1234 myapp
```

> **Note:** Avoid putting real passwords or API keys directly in shell commands or Dockerfiles.

---

# 17. Docker Volumes

Volumes are used to store data outside the container's writable layer.

This is useful because container data can otherwise be lost when a container is removed.

## Create a Volume

```bash
docker volume create <volume-name>
```

Example:

```bash
docker volume create mydata
```

---

## List Volumes

```bash
docker volume ls
```

---

## Inspect a Volume

```bash
docker volume inspect mydata
```

---

## Use a Volume with a Container

```bash
docker run -v mydata:/data ubuntu
```

Here:

* `mydata` = Docker volume
* `/data` = Directory inside the container

---

## Remove a Volume

```bash
docker volume rm mydata
```

---

## Remove Unused Volumes

```bash
docker volume prune
```

---

# 18. Bind Mounts

A bind mount connects a directory from your computer to a directory inside the container.

Syntax:

```bash
docker run -v <host-path>:<container-path> <image>
```

Example:

```bash
docker run -v ~/myproject:/app ubuntu
```

This connects:

```text
~/myproject
```

on the host to:

```text
/app
```

inside the container.

---

# 19. Docker Networks

Networks allow containers to communicate with each other.

## List Networks

```bash
docker network ls
```

---

## Create a Network

```bash
docker network create <network-name>
```

Example:

```bash
docker network create mynetwork
```

---

## Run Container on a Network

```bash
docker run -d --network mynetwork --name app nginx
```

---

## Inspect a Network

```bash
docker network inspect mynetwork
```

---

## Connect a Container to a Network

```bash
docker network connect mynetwork <container-name>
```

Example:

```bash
docker network connect mynetwork app
```

---

## Disconnect a Container

```bash
docker network disconnect mynetwork app
```

---

## Remove a Network

```bash
docker network rm mynetwork
```

---

# 20. Dockerfile

A Dockerfile contains instructions used to build a Docker image.

Example Dockerfile:

```dockerfile
FROM python:3.12

WORKDIR /app

COPY . .

RUN pip install -r requirements.txt

CMD ["python", "app.py"]
```

---

# 21. Build a Docker Image

```bash
docker build -t <image-name> .
```

Example:

```bash
docker build -t myapp .
```

Here:

* `docker build` = Build an image
* `-t myapp` = Give the image a name
* `.` = Use the current directory as the build context

---

## Build with a Specific Dockerfile

```bash
docker build -f Dockerfile.dev -t myapp .
```

---

# 22. Run Your Custom Image

After building an image:

```bash
docker run myapp
```

For an application that uses port 5000:

```bash
docker run -p 5000:5000 myapp
```

---

# 23. Tag Docker Images

Tags are used to give images versions or repository names.

```bash
docker tag <image> <repository>:<tag>
```

Example:

```bash
docker tag myapp myusername/myapp:v1
```

---

# 24. Docker Hub

Docker Hub is a public registry where Docker images can be stored and shared.

## Login to Docker Hub

```bash
docker login
```

Docker will ask for your Docker Hub credentials.

---

## Push an Image

```bash
docker push <username>/<repository>:<tag>
```

Example:

```bash
docker push myusername/myapp:v1
```

---

## Pull an Image from Docker Hub

```bash
docker pull myusername/myapp:v1
```

---

# 25. Search Docker Hub

```bash
docker search <image-name>
```

Example:

```bash
docker search nginx
```

This searches for Docker images available through Docker Hub.

---

# 26. Copy Files Between Host and Container

## Copy File from Host to Container

```bash
docker cp <host-file> <container>:<path>
```

Example:

```bash
docker cp app.py mycontainer:/app/
```

---

## Copy File from Container to Host

```bash
docker cp <container>:<path> <host-path>
```

Example:

```bash
docker cp mycontainer:/app/log.txt .
```

---

# 27. Rename a Container

```bash
docker rename <old-name> <new-name>
```

Example:

```bash
docker rename oldcontainer newcontainer
```

---

# 28. Pause and Unpause Containers

## Pause a Container

```bash
docker pause <container-name>
```

Example:

```bash
docker pause mycontainer
```

---

## Unpause a Container

```bash
docker unpause <container-name>
```

Example:

```bash
docker unpause mycontainer
```

---

# 29. Kill a Container

```bash
docker kill <container-name>
```

Example:

```bash
docker kill mycontainer
```

`docker kill` immediately sends a kill signal to the container, while `docker stop` normally gives the application time to shut down gracefully.

---

# 30. Docker System Commands

## Show Docker Disk Usage

```bash
docker system df
```

This shows how much disk space Docker is using.

---

## Remove Unused Docker Resources

```bash
docker system prune
```

This can remove unused:

* Containers
* Networks
* Images
* Build cache

Docker will ask for confirmation.

---

## Remove More Unused Images

```bash
docker system prune -a
```

> **Warning:** This can remove unused images that you may want later. Use it carefully.

---

# 31. Docker Compose

Docker Compose is used to define and run applications containing multiple containers.

For example, a web application may have:

```text
Web Application
       |
       +---- Frontend
       |
       +---- Backend
       |
       +---- Database
```

A Compose file is usually named:

```text
compose.yaml
```

or:

```text
docker-compose.yml
```

---

## Start Services

```bash
docker compose up
```

---

## Start Services in Background

```bash
docker compose up -d
```

---

## Stop Services

```bash
docker compose down
```

---

## View Compose Services

```bash
docker compose ps
```

---

## View Compose Logs

```bash
docker compose logs
```

---

## Follow Compose Logs

```bash
docker compose logs -f
```

---

## Build Compose Services

```bash
docker compose build
```

---

# 32. Common Docker Command Summary

| Command                 | Purpose                          |
| ----------------------- | -------------------------------- |
| `docker --version`      | Check Docker version             |
| `docker info`           | Display Docker information       |
| `docker --help`         | Show Docker help                 |
| `docker images`         | List images                      |
| `docker pull`           | Download an image                |
| `docker push`           | Upload an image                  |
| `docker build`          | Build an image                   |
| `docker rmi`            | Remove an image                  |
| `docker run`            | Create and run a container       |
| `docker ps`             | Show running containers          |
| `docker ps -a`          | Show all containers              |
| `docker start`          | Start a container                |
| `docker stop`           | Stop a container                 |
| `docker restart`        | Restart a container              |
| `docker rm`             | Remove a container               |
| `docker exec`           | Run command inside container     |
| `docker logs`           | View container logs              |
| `docker inspect`        | View detailed information        |
| `docker stats`          | View resource usage              |
| `docker cp`             | Copy files                       |
| `docker rename`         | Rename a container               |
| `docker pause`          | Pause a container                |
| `docker unpause`        | Resume a container               |
| `docker kill`           | Immediately stop a container     |
| `docker volume ls`      | List volumes                     |
| `docker volume create`  | Create a volume                  |
| `docker volume rm`      | Remove a volume                  |
| `docker network ls`     | List networks                    |
| `docker network create` | Create a network                 |
| `docker network rm`     | Remove a network                 |
| `docker system df`      | Check Docker disk usage          |
| `docker system prune`   | Remove unused resources          |
| `docker compose up`     | Start Compose services           |
| `docker compose down`   | Stop and remove Compose services |

---

# 33. Important Docker Options

Some options are frequently used with Docker commands.

| Option      | Meaning                  | Example                              |
| ----------- | ------------------------ | ------------------------------------ |
| `-d`        | Run in background        | `docker run -d nginx`                |
| `-it`       | Interactive terminal     | `docker run -it ubuntu`              |
| `-p`        | Map ports                | `docker run -p 8080:80 nginx`        |
| `--name`    | Give container a name    | `docker run --name app nginx`        |
| `-e`        | Set environment variable | `docker run -e ENV=dev app`          |
| `-v`        | Mount volume/directory   | `docker run -v data:/app/data app`   |
| `--network` | Select network           | `docker run --network mynetwork app` |
| `-f`        | Specify Dockerfile       | `docker build -f Dockerfile.dev .`   |
| `-t`        | Assign image tag/name    | `docker build -t myapp .`            |

---

# 34. Basic Docker Workflow

A common Docker workflow is:

```text
Write Application
       ↓
Create Dockerfile
       ↓
Build Docker Image
       ↓
Run Docker Container
       ↓
Test Application
       ↓
View Logs / Debug
       ↓
Push Image to Registry
```

Example:

```bash
# Build image
docker build -t myapp .

# Run container
docker run -d --name myapp-container -p 8080:8080 myapp

# Check container
docker ps

# View logs
docker logs myapp-container

# Stop container
docker stop myapp-container

# Remove container
docker rm myapp-container
```

---

# 35. Docker Command Cheat Sheet

```bash
# Docker version
docker --version

# Docker information
docker info

# List images
docker images

# Pull image
docker pull ubuntu

# Run container
docker run ubuntu

# Run interactively
docker run -it ubuntu

# Run in background
docker run -d nginx

# List running containers
docker ps

# List all containers
docker ps -a

# Start container
docker start mycontainer

# Stop container
docker stop mycontainer

# Restart container
docker restart mycontainer

# Remove container
docker rm mycontainer

# Remove image
docker rmi ubuntu

# Execute command
docker exec mycontainer ls

# Open container shell
docker exec -it mycontainer bash

# View logs
docker logs mycontainer

# View live logs
docker logs -f mycontainer

# Inspect container
docker inspect mycontainer

# View resource usage
docker stats

# Build image
docker build -t myapp .

# Run application with port
docker run -d -p 8080:80 nginx

# Create volume
docker volume create mydata

# List volumes
docker volume ls

# Create network
docker network create mynetwork

# List networks
docker network ls

# Check disk usage
docker system df

# Clean unused resources
docker system prune

# Start Compose
docker compose up

# Start Compose in background
docker compose up -d

# Stop Compose
docker compose down
```

---

# 36. Important Notes

1. A **Docker image** is a template.
2. A **Docker container** is an instance of an image.
3. `docker ps` shows running containers.
4. `docker ps -a` shows all containers.
5. `docker pull` downloads an image.
6. `docker build` creates an image from a Dockerfile.
7. `docker run` creates and starts a container.
8. `docker stop` stops a container gracefully.
9. `docker rm` removes a container.
10. `docker rmi` removes an image.
11. Volumes are useful for persistent data.
12. Docker networks allow containers to communicate.
13. Docker Compose helps manage multiple containers.
14. Be careful with `docker system prune` because it can remove resources you still need.

---

# 37. Conclusion

Docker makes it easier to package, run, and manage applications in isolated containers. The most important commands for beginners are:

```bash
docker pull
docker images
docker run
docker ps
docker ps -a
docker start
docker stop
docker rm
docker exec
docker logs
docker build
docker rmi
docker volume
docker network
docker compose
```

Learning these commands provides a strong foundation for working with Docker and containerized applications.

