# Docker Day 01 - Installation, Images, Dockerfile & Basic Commands

**Date:** 31-Jul-2026

---

# 🎯 Objective

Today I learned how to install Docker on Ubuntu, understand Docker Images, create a Dockerfile, build Docker images, and troubleshoot common Docker errors.

---

# 📚 Topics Learned

- What is Docker?
- Docker Installation on Ubuntu
- Docker Images
- Official Images vs Repository Images
- Dockerfile
- Docker Build Process
- Docker Hub
- Docker Image Push
- Docker Build Context
- Basic Docker Troubleshooting

---

# 🛠 Commands Practiced

## Update Package Repository

```bash
sudo apt update -y
```

---

## Install Docker

```bash
sudo apt install docker.io -y
```

---

## Verify Docker Installation

```bash
docker -v
```

```bash
docker --version
```

---

## View Docker Images

```bash
docker images
```

---

## Pull Ubuntu Image

```bash
docker pull ubuntu
```

---

## Pull Jenkins Image

```bash
docker pull jenkins/jenkins
```

---

## Docker Build

```bash
docker build -t ambikadevops/mavenwebapplication:1.0.0 .
```
<img width="1112" height="617" alt="image" src="https://github.com/user-attachments/assets/6e346488-398e-47c0-9af2-f9282f3fa972" />


## Update the Maven Compiler Plugin in `pom.xml`

Updated the Maven Compiler Plugin version in `pom.xml` to make the project compatible with the installed JDK version.

<img width="851" height="615" alt="pom.xml update" src="https://github.com/user-attachments/assets/3e85b200-c6f7-41c0-bcbc-02d882580bf7" />

---

## Build the Maven Project

Run the following command to compile the project and generate the WAR file.

```bash
mvn clean package
```

### Initial Build Failure

The build failed because the Maven Compiler Plugin version specified in `pom.xml` was outdated and incompatible with the installed JDK version.

<img width="1366" height="696" alt="Maven Build Failure" src="https://github.com/user-attachments/assets/b699eb9f-b75d-435c-b218-3fc652bef19c" />

---

## Build Successful

After updating the Maven Compiler Plugin version in `pom.xml`, the Maven build completed successfully.

The following actions were performed successfully:

- Created the `target/` directory.
- Generated the application WAR file (`maven-web-application.war`).
- Prepared the WAR file for deployment to Tomcat or for building a Docker image.

<img width="1366" height="704" alt="Maven Build Success" src="https://github.com/user-attachments/assets/8fd42a3e-ae18-4728-b487-e6a9634f905b" />

---

## Key Learning

- The `pom.xml` file manages project dependencies and build plugins.
- The Maven Compiler Plugin version must be compatible with the installed JDK version.
- Running `mvn clean package` compiles the project and generates the deployable WAR file inside the `target/` directory.
- The generated WAR file is used for deployment to Tomcat or for creating a Docker image.

---

## Docker Login

```bash
docker login
```

---

## Docker Push

```bash
docker push ambikadevops/mavenwebapplication:1.0.0
```

---

## Add Current User to Docker Group

```bash
sudo usermod -aG docker ubuntu
```

or

```bash
sudo usermod -aG docker $USER
```

---

## Apply Group Changes

```bash
newgrp docker
```

---

## Docker Cleanup Commands

### Remove Stopped Containers

```bash
docker container prune -f
```

### Remove Unused Images

```bash
docker image prune -a -f
```
<img width="1118" height="357" alt="image" src="https://github.com/user-attachments/assets/72819389-9a6e-453b-8e85-f2f0328b5130" />


### Remove Unused Volumes

```bash
docker volume prune -f
```

### Remove Unused Networks

```bash
docker network prune -f
```

### Remove Everything

```bash
docker system prune -a --volumes -f
```

---

# 📄 Dockerfile Practiced

```dockerfile
FROM tomcat:9.0.100-jdk8-corretto
COPY target/maven-web-application.war /usr/local/tomcat/webapps/
```
<img width="1337" height="705" alt="Screenshot 2026-08-01 014713" src="https://github.com/user-attachments/assets/a7fe46f4-f961-49aa-a86a-d00246777dc1" />

---

# 🧠 Concepts Understood

## Docker

Docker is a containerization platform used to package an application along with its dependencies into a portable container.

---

## Docker Image

A Docker Image is a read-only template used to create containers.

Examples:

- ubuntu
- nginx
- mysql
- tomcat

---

## Docker Container

A running instance of a Docker Image.

---

## Dockerfile

A text file containing instructions to build a Docker Image.

---

## Docker Hub

Docker Hub is a cloud-based registry used to store and share Docker Images.

<img width="1125" height="598" alt="Screenshot 2026-08-01 011900" src="https://github.com/user-attachments/assets/879fab17-1016-48c3-9925-7854ca9adf0d" />

<img width="1366" height="768" alt="Screenshot 2026-08-01 012211" src="https://github.com/user-attachments/assets/3ff660a6-f613-4987-b644-b354f222b4c3" />

---

# 🐞 Errors Faced & Troubleshooting

## Error

```text
docker: command not found
```

### Reason

Docker was not installed.

### Resolution

```bash
sudo apt install docker.io -y
```

---

## Error

```text
permission denied while trying to connect to docker.sock
```

### Reason

Current user was not added to the Docker group.

### Resolution

```bash
sudo usermod -aG docker ubuntu
```

Logout and login again.

---

## Error

```text
COPY failed: file not found
```

### Reason

Wrong build context or incorrect WAR file path.

### Resolution

Verify:

```bash
pwd
```

```bash
ls target/
```

---

## Error

```text
Dockerfile not found
```

### Reason

Dockerfile was created in the wrong directory.

### Resolution

Move Dockerfile to the project root.

---

# 💡 Interview Takeaways

- Learned Docker installation on Ubuntu.
- Understood Docker Images and Containers.
- Learned the purpose of Dockerfile.
- Practiced building Docker Images.
- Learned Docker Hub login and image push.
- Understood Docker build context.
- Practiced troubleshooting common Docker errors.

---

# 🚀 Real-Time DevOps Workflow

```text
Developer
    ↓
GitHub
    ↓
Jenkins
    ↓
Maven Build
    ↓
WAR File
    ↓
Dockerfile
    ↓
Docker Build
    ↓
Docker Image
    ↓
Docker Hub
    ↓
Production Server
```

---

# 📌 Key Learning

Today I successfully learned the fundamentals of Docker, installed Docker on Ubuntu, worked with Docker Images, Dockerfile, Docker Hub, and practiced troubleshooting common Docker issues encountered during image creation.
