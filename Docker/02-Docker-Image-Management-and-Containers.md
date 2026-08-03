# Docker Day 02 - Docker Image Management & Container Operations

**Date:** 03-Aug-2026

---

# 🎯 Objective

Today I learned how to work with Docker images, Docker Hub, containers, image transfer between servers, image tagging, and Docker cleanup commands.

---

# 📚 Topics Covered

- Docker Build
- Docker Pull
- Docker Push
- Docker History
- Docker Run
- Port Mapping
- Docker PS
- Docker Image Removal
- Docker Container Removal
- Docker Tag
- Docker Save & Load
- Docker Image Inspect
- Docker Disk Usage
- Docker Cleanup Commands
- Alpine Images

---

# 🛠 Commands Practiced

## Build Docker Image

```bash
docker build -t ambikadevops/mavenwebapplication:1.0.0 .
```

### Syntax

```text
docker build -t <dockerhub-username>/<image-name>:<tag> .
```

Example:

- Docker Hub Username : ambikadevops
- Image Name : mavenwebapplication
- Tag : 1.0.0
- `.` → Current directory (Build Context)

---

## Pull Image from Docker Hub

```bash
docker pull ambikadevops/mavenwebapplication:1.0.0
```

Downloads an image from Docker Hub to the local machine.

---

## Push Image to Docker Hub

```bash
docker push ambikadevops/mavenwebapplication:1.0.0
```

Uploads a local Docker image to Docker Hub.

---

## View Image History

```bash
docker history <image-id>
```

Displays all image layers.

---

## Run a Container

```bash
docker run -d -p 8080:8080 --name mavenwebappone ambikadevops/mavenwebapplication:1.0.0
```
<img width="1366" height="768" alt="Screenshot 2026-08-03 222944" src="https://github.com/user-attachments/assets/7c0bc42c-d4cf-4089-acc8-70c23d5b2662" />

### Parameters

| Option | Description |
|---------|-------------|
| `-d` | Detached mode |
| `-p` | Port mapping |
| `8080:8080` | Host Port : Container Port |
| `--name` | Container name |

---

## List Running Containers

```bash
docker ps
```
<img width="1366" height="722" alt="Screenshot 2026-08-03 223007" src="https://github.com/user-attachments/assets/154cfede-44fb-449e-a749-acdb0a29765f" />

or

```bash
docker container ls
```

---

## List All Containers

```bash
docker ps -a
```

Shows running and stopped containers.

---

## Stop Container

```bash
docker stop <container-id>
```

---

## Remove Container

```bash
docker rm <container-id>
```

Force remove

```bash
docker rm -f <container-id>
```

---

## Remove Docker Image

```bash
docker rmi <image-id>
```

or

```bash
docker rmi <image-name>:<tag>
```

---

## List Only Image IDs

```bash
docker images -aq
```

---

## Remove All Images

```bash
docker rmi $(docker images -aq)
```

Force remove

```bash
docker rmi -f $(docker images -aq)
```

---

## Inspect Docker Image

```bash
docker image inspect <image-id>
```

Displays complete metadata of the image.

---

## Tag Docker Image

```bash
docker tag <source-image> <target-image>
```

Example

```bash
docker tag ubuntu ambikaubuntu
```

Docker tag creates another name for the same image.

---

## Save Docker Image

```bash
docker save -o webapp.tar ambikadevops/mavenwebapplication:1.0.0
```

Exports the Docker image into a `.tar` file.

---

## Load Docker Image

```bash
docker load -i webapp.tar
```

Imports the image from a `.tar` file.

---

## Check Docker Disk Usage

```bash
docker system df
```

Shows Docker disk space usage.

---

# Docker Cleanup Commands

## Remove Stopped Containers

```bash
docker container prune
```

---

## Remove Unused Images

```bash
docker image prune
```

---

## Remove Unused Networks

```bash
docker network prune
```

---

## Remove Unused Volumes

```bash
docker volume prune
```

---

## Remove Everything

```bash
docker system prune
```

---

# 🌐 Real-Time DevOps Use Cases

## Docker Hub

Used to share Docker images between multiple servers.

Example:

```text
Developer Server
      │
docker push
      │
Docker Hub
      │
docker pull
      │
Production Server
```

---

## Docker Save & Load

When internet access is unavailable:

```text
Build Server
      │
docker save
      │
webapp.tar
      │
scp
      │
Deployment Server
      │
docker load
```
<img width="1366" height="768" alt="Screenshot 2026-08-03 234424" src="https://github.com/user-attachments/assets/87e8f5bb-1d57-4a76-b2ef-3bbb1ec39b59" />

---

## Docker Tag

Useful when:

- Changing repository names
- Version management
- Preparing images for Docker Hub

---

## Docker Inspect

Used to check:

- Image metadata
- Environment variables
- Labels
- Layers
- Configuration

---

# 💡 Important Notes

- A single Docker image can create multiple containers.
- Every container must have a unique container name.
- Multiple containers cannot use the same host port simultaneously.
- Remove containers before removing the associated image.
- `docker images -aq` returns only image IDs.
- Alpine images are lightweight and commonly used to reduce image size.

---

# 🐞 Troubleshooting

## Permission Denied

```text
permission denied while trying to connect to docker.sock
```

Solution

```bash
sudo usermod -aG docker ubuntu
newgrp docker
```

---

## Dockerfile Not Found

```text
unable to evaluate symlinks in Dockerfile path
```

Reason

Dockerfile not present in the current directory.

---

## COPY Failed

```text
COPY failed: file not found
```

Reason

Incorrect build context or incorrect file path.

---

# 📌 Key Learnings

- Learned Docker image lifecycle.
- Understood Docker Hub workflow.
- Practiced Docker image tagging.
- Learned Docker save and load for offline deployments.
- Practiced Docker cleanup commands.
- Understood container lifecycle management.
- Learned image inspection and history.
- Understood Docker image sharing between servers.
