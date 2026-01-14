# Docker Main Notes:
## 🐳 1. What is Docker?
### Ans: Docker is a containerization platform that allows you to build, run, and manage applications in lightweight, portable containers.
* Containers run consistently across different environments like development, testing, and production.
* A container packages an application and all its dependencies (libraries, binaries, configuration files) so it runs consistently across environments.

## ✅ Key benefits:
* Consistency across development → production
* Lightweight and fast (uses host OS kernel)
* Easy scalability and deployment
* Version-controlled environments

## 📄 2. What is a Dockerfile?
### Ans: A Dockerfile is a text file that contains a series of instructions for building a Docker image.
* Each instruction defines how the image is built — for example, what base image to use, what dependencies to install, and what command to run.

## 🧩 Example:
* #### # Start from a base image
* FROM python:3.10

* #### # Set working directory
* WORKDIR /app

* #### # Copy code into container
* COPY . .

* #### # Install dependencies
* RUN pip install -r requirements.txt

* #### # Command to run app
* CMD ["python", "app.py"]

## 🧱 3. What is a Docker Image?
### Ans: A Docker Image is a read-only template used to create containers.
* It includes everything needed to run an application — code, runtime, libraries, environment variables, and configuration files.
### You can think of it as a blueprint for containers.
 * Built using a Dockerfile
 * Stored locally or on a Docker registry
 * Immutable (cannot be changed once built)

## 📦 4. What is a Docker Container?
### Ans: A Docker Container is a running instance of a Docker image.
* It’s an isolated environment that runs your application with its own file system, networking, and process space — but shares the host OS kernel.
## 🧩 Example commands:
### # Run a container
* docker run -d -p 8080:80 nginx

### # List running containers
* docker ps

### # Stop and remove a container
* docker stop <container_id>
* docker rm <container_id>

## 🌐 5. What is Docker Networking?
### Ans: Docker Networking allows containers to communicate with each other, the host, or external systems.

## 🕸️ Types of Docker Networks:
* bridge (default) → Containers communicate on a private network
* host → Container shares host’s network stack
* none → No network (isolated container)
* overlay → Used for multi-host communication in Swarm or Kubernetes

## 🧩 Example:
* docker network create mynetwork
* docker run -d --network=mynetwork myapp

## 💾 6. What is Docker Volumes and Storage?
### Ans: Docker volume is a persistent storage mechanism used to store data outside the container lifecycle. Even if a container is deleted, the data remains.
* By default, container data is temporary — deleted when the container is removed.
* Volumes allow data to survive container restarts or be shared between containers.

## 🧩 Example:
### # Create and use a volume
* docker volume create myvolume
* docker run -v myvolume:/app/data myapp

## 📁 Types of Storage:
### 1. Volumes → Managed by Docker (best practice)
### 2. Bind Mounts → Use host system’s directories
### 3. Tmpfs Mounts → Stored in memory only

## ⚙️ 7. What is Docker Compose?
### Ans: Docker Compose is a tool to define and run multi-container applications using a simple YAML file (docker-compose.yml).
* You can specify services, networks, and volumes — and bring them all up with one command.

## 🧩 Example:
* version: "3"
* services:
  * web:
    * image: nginx
    * ports:
      * - "8080:80"
  * app:
    * build: .
    * depends_on:
      * - db
  * db:
    * image: mysql
    * environment:
      * MYSQL_ROOT_PASSWORD: example
### RUN This:--> docker-compose up -d

## 🏪 8. What is Docker Registry?
### Ans: A Docker Registry is a repository where Docker images are stored and shared.

### 📦 Types:
* Public Registry: Docker Hub
* Private Registry: Self-hosted or cloud-based (AWS ECR, GCP Artifact Registry, Azure ACR)

### 🧩 Example:
### # Login and push image
* docker login
* docker tag myapp:latest myrepo/myapp:v1
* docker push myrepo/myapp:v1

## 🧰 9. What is Multi-Stage Docker Build?
### Ans: Multi-stage builds help you optimize image size by using multiple FROM instructions in your Dockerfile.
* You can use one stage to build your app (with dependencies and tools) and another stage to copy only the final output.

## 🧩 Example:
#### # Build stage
* FROM golang:1.20 as builder
* WORKDIR /app
* COPY . .
* RUN go build -o myapp

#### # Final stage (small runtime image)
* FROM alpine:latest
* COPY --from=builder /app/myapp /usr/local/bin/myapp
* CMD ["myapp"]
👉 This reduces image size and improves performance.

## 📊 10. What is Monitoring and Logging in Docker?
### Ans: Monitoring and Logging are used to track container performance, resource usage, and logs.

## 🧾 Logging
* Docker captures container logs via the stdout/stderr streams.
* You can view logs with:
* docker logs <container_id>
* Logs can be forwarded to systems like:
    * ELK Stack (Elasticsearch, Logstash, Kibana)
    * Fluentd
    * Splunk

### 📈 Monitoring
* Tools to monitor containers’ CPU, memory, network, and disk:
   * Docker Stats (basic built-in)
   * Prometheus + Grafana
   * cAdvisor
   * Datadog, New Relic, Sysdig
