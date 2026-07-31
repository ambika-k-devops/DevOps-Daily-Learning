ఈరోజు చేసిన commands, వాటి purpose, ఎప్పుడు వాడాలి అన్నవి మొత్తం క్రింద ఉన్నాయి. ఇవి ఈరోజు session లో చేసిన వాటి ఆధారంగా తయారు చేశాను. 

# 1. Docker Installation

### Package List Update

```bash
sudo apt update -y
```

**ఎందుకు?**

* Ubuntu package list update అవుతుంది.
* కొత్త packages ఏవి available లో ఉన్నాయో తెలుసుకుంటుంది.
* ఏ software install చేసే ముందు సాధారణంగా run చేస్తారు.

---

### Docker Install

```bash
sudo apt install docker.io -y
```

**ఎందుకు?**

Ubuntu server లో Docker install చేయడానికి.

---

### Docker Version Check

```bash
docker -v
```

లేదా

```bash
docker --version
```

**ఎందుకు?**

Docker install అయ్యిందా లేదా check చేయడానికి.

---

# 2. Git Commands

### Repository Clone

```bash
git clone https://github.com/kkdevopsb4/maven-web-app-project-kk-funda
```

**ఎందుకు?**

GitHub లో ఉన్న project ని local server కి download చేయడానికి.

---

### Files Check

```bash
ls -lrth
```

**ఎందుకు?**

Current directory లో files/folders చూడడానికి.

**Options**

* `-l` → Detailed information
* `-r` → Reverse order
* `-t` → Time ఆధారంగా sort
* `-h` → Human readable size

---

# 3. Directory Commands

### Folder లోకి వెళ్ళడానికి

```bash
cd maven-web-app-project-kk-funda
```

---

### ఒక level వెనక్కి రావడానికి

```bash
cd ..
```

---

### Current Location తెలుసుకోవడానికి

```bash
pwd
```

**ఎందుకు?**

నేను ప్రస్తుతం ఏ folder లో ఉన్నాను తెలుసుకోవడానికి.

---

# 4. Maven Commands

### Maven Install

```bash
sudo apt install maven -y
```

---

### Build Project

```bash
mvn clean package
```

**ఎందుకు?**

Java project compile చేసి

```text
.jar

లేదా

.war
```

generate చేస్తుంది.

Output

```text
target/
```

folder.

---

### Build తర్వాత

```bash
ls target/
```

**ఎందుకు?**

WAR file generate అయిందా check చేయడానికి.

---

# 5. Docker Commands

### Images చూడడానికి

```bash
docker images
```

**ఎందుకు?**

Local machine లో ఉన్న Docker Images list.

---

### Ubuntu Image Download

```bash
docker pull ubuntu
```

---

### Jenkins Image Download

```bash
docker pull jenkins/jenkins
```

---

### Docker Build

```bash
docker build -t ambikadevops/mavenwebapplication:1.0.0 .
```

**ఎందుకు?**

Dockerfile ఉపయోగించి Docker Image create చేయడానికి.

---

### Docker Push

```bash
docker push ambikadevops/mavenwebapplication:1.0.0
```

**ఎందుకు?**

Docker Hub కి image upload చేయడానికి.

---

### Docker Login

```bash
docker login
```

**ఎందుకు?**

Docker Hub authentication.

---

# 6. Docker Permission

### User ని docker group లో add చేయడం

```bash
sudo usermod -aG docker ubuntu
```

లేదా

```bash
sudo usermod -aG docker $USER
```

**ఎందుకు?**

`sudo` లేకుండా Docker commands run చేయడానికి.

---

### New Group Apply

```bash
newgrp docker
```

లేదా

Logout చేసి Login.

---

# 7. Docker Clean Commands

### Containers Remove

```bash
docker container prune -f
```

---

### Images Remove

```bash
docker image prune -a -f
```

---

### Volumes Remove

```bash
docker volume prune -f
```

---

### Networks Remove

```bash
docker network prune -f
```

---

### Complete Cleanup

```bash
docker system prune -a --volumes -f
```

---

# 8. Folder Delete

Folder delete

```bash
rm -rf maven-web-app-project-kk-funda
```

**ఎందుకు?**

Folder పూర్తిగా delete చేయడానికి.

---

# 9. File Content చూడడానికి

Dockerfile

```bash
cat Dockerfile
```

---

Line Numbers తో

```bash
cat -n Dockerfile
```

---

# 10. vi Editor

### Save & Exit

```
:wq
```

---

### Exit Without Saving

```
:q!
```

---

### Copy Current Line

```
yy
```

---

### Copy Entire File

```
:%y
```

---

### Paste

```
p
```

---

# 11. System Monitoring

CPU, Memory, Processes

```bash
top
```

---

# 12. Dockerfile

```dockerfile
FROM tomcat:9.0.100-jdk8-corretto
COPY target/maven-web-application.war /usr/local/tomcat/webapps/
```

---

# 13. Debug Commands (చాలా Important)

Project build fail అయితే

```bash
pwd
```

ఎక్కడ ఉన్నావో తెలుసుకోవడానికి.

---

```bash
ls -lrth
```

Files చూడడానికి.

---

```bash
ls target/
```

WAR file ఉందా చూడడానికి.

---

```bash
cat Dockerfile
```

Dockerfile verify చేయడానికి.

---

```bash
docker images
```

Image build అయిందా చూడడానికి.

---

# 14. Errors నువ్వు ఎదుర్కొన్నవి & Root Cause

| Error                                                   | Root Cause                             | Solution                                        |
| ------------------------------------------------------- | -------------------------------------- | ----------------------------------------------- |
| `docker: command not found`                             | Docker install కాలేదు                  | `sudo apt install docker.io -y`                 |
| `mvn: command not found`                                | Maven install కాలేదు                   | `sudo apt install maven -y`                     |
| `permission denied while trying to connect docker.sock` | User docker group లో లేడు              | `sudo usermod -aG docker ubuntu` → Logout/Login |
| `there is no POM in this directory`                     | Wrong directory                        | `cd project-folder`                             |
| `COPY failed: file not found`                           | Wrong build context లేదా WAR file లేదు | `target/` & Dockerfile verify చేయి              |
| `Dockerfile: no such file or directory`                 | Dockerfile project root లో లేదు        | Dockerfile ని project root కి move చేయి         |

---

# ఈరోజు Complete DevOps Flow

```text
EC2 Login
      ↓
sudo apt update
      ↓
Install Docker
      ↓
Install Maven
      ↓
Git Clone
      ↓
cd Project
      ↓
mvn clean package
      ↓
target/*.war
      ↓
Create Dockerfile
      ↓
docker build
      ↓
docker images
      ↓
docker login
      ↓
docker push
```

## Interview Tip

ఈరోజు నువ్వు నేర్చుకున్న commands కంటే **ప్రతి command ఎందుకు వాడుతున్నామో** అర్థం చేసుకోవడం ఇంకా ముఖ్యమైనది. Interview లో interviewer చాలాసార్లు command కంటే **"ఈ command ఎందుకు వాడారు?"**, **"ఈ error ఎందుకు వచ్చింది?"**, **"దాన్ని ఎలా troubleshoot చేస్తారు?"** అని అడుగుతారు. ఈరోజు practice చేసిన errors (`docker.sock permission`, `no POM`, `COPY failed`, `Dockerfile not found`) ఇవన్నీ real-world DevOps troubleshooting examples.
