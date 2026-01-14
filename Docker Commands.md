# 🧰 Basic Commands Of Docker
## 🔹 Basic Docker Commands:-
* docker --version	>>>>> Check Docker version
* docker info	 >>>>> Show system-wide Docker information
* docker images	 >>>>> List all Docker images
* docker ps	 >>>>> List running containers
* docker ps -a	>>>>> List all containers (including stopped)
* docker pull <image_name>  >>>>> Download an image from Docker Hub
* docker run <image_name>	>>>>> Run a container from an image
* docker run -d <image>	 >>>>> Run container in detached (background) mode
* docker run -it <image> /bin/bash >>>>>  Run container interactively
* docker stop <container_id> >>>>> Stop a running container
* docker start <container_id>	>>>>>  Start a stopped container
* docker restart <container_id>	 >>>>> Restart a container
* docker rm <container_id>	>>>>> Remove a container
* docker rmi <image_id>	 >>>>>  Remove an image
* docker exec -it <container_id> >>>>> bash	Enter a running container shell
* docker logs <container_id>	>>>>> View container logs
* docker build -t <image_name> .	>>>>> Build image from Dockerfile in current dir
* docker tag <source_image> <new_name> >>>>>  Rename/tag an image
* docker network ls	 >>>>> List Docker networks
* docker volume ls	 >>>>> List Docker volumes

## 🔹 Dockerfile Commands:-
### These are instructions used inside a Dockerfile (not CLI commands):
* FROM	>>>>> Set base image (e.g., FROM ubuntu:20.04)
* WORKDIR	>>>>> Set working directory inside container
* COPY	>>>>> Copy files from host to container
* ADD	 >>>>> Similar to COPY, but supports URLs and archives
* RUN	>>>>> Execute a command during build (e.g., RUN apt-get install)
* CMD	>>>>> Command that runs when container starts
* ENTRYPOINT >>>>>	Set main executable for the container
* EXPOSE	>>>>> Document the port the container listens on
* ENV	>>>>> Set environment variables
* VOLUME >>>>> Create mount point for volumes
* LABEL	>>>>> Add metadata (like maintainer info)

## 🔹 Docker Compose Basic Commands:-
* docker-compose --version >>>>>	Check Docker Compose version
* docker-compose up	  >>>>> Start all services defined in docker-compose.yml
* docker-compose up -d	  >>>>> Start services in detached (background) mode
* docker-compose down	  >>>>> Stop and remove all services/containers
* docker-compose ps	 >>>>> List all running services
* docker-compose build	 >>>>> Build images defined in Compose file
* docker-compose restart	>>>>> Restart services
* docker-compose logs	 >>>>> View logs from all services
* docker-compose exec <service> bash	>>>>> Open shell inside a running service container
* docker-compose stop	 >>>>> Stop services without removing them
* docker-compose rm	 >>>>> Remove stopped services

## Note: This Command is Used For Making Container to Docker images
* docker commit <containerid> <imagename>;tag



