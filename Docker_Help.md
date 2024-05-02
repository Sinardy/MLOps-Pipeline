# Basic Docker Commands

Below is a list of commonly used Docker commands for managing containers and images.

## 1. Check Docker Version

To check the version of Docker installed on your system, use:

```bash
docker --version
```

## 2. List Docker Images

To list all Docker images available locally, execute:

```bash
docker images
```

## 3. Pull Docker Image

To download a Docker image from a registry, use:

```bash
docker pull IMAGE_NAME[:TAG]
```

Example:

```bash
docker pull nginx:latest
```

## 4. Run Docker Container

To run a Docker container from an image, use:

```bash
docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
```

Example:

```bash
docker run -d -p 8080:80 nginx
```

## 5. List Running Containers

To list all running Docker containers, execute:

```bash
docker ps
```

## 6. Stop Docker Container

To stop a running Docker container, use:

```bash
docker stop CONTAINER_ID
```

## 7. Start Docker Container

To start a stopped Docker container, use:

```bash
docker start CONTAINER_ID
```

## 8. Restart Docker Container

To restart a Docker container, use:

```bash
docker restart CONTAINER_ID
```

## 9. Remove Docker Container

To remove a Docker container, use:

```bash
docker rm CONTAINER_ID
```

## 10. Remove Docker Image

To remove a Docker image, use:

```bash
docker rmi IMAGE_ID
```
