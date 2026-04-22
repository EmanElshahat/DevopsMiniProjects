# 🚀 CI/CD Pipeline for Java Login Application using GitHub Actions
## 📌 Project Overview
This project demonstrates how to implement a complete CI/CD pipeline using GitHub Actions for a Spring Boot Java application.

The pipeline automates the process of building the application, containerizing it using Docker, pushing the image to Docker Hub, and deploying it automatically to an AWS EC2 instance.

It also includes versioning and rollback capabilities for better release management.

---
## 🛠️ Tools Used
- Spring Boot (Java)
- Maven
- Docker
- Docker Hub
- GitHub Actions
- AWS EC2
- Ubuntu Linux

---
## ⚙️ CI/CD Pipeline Workflow
 The pipeline is triggered on:
- Push to `main` branch (automatic deployment)
- Manual trigger using workflow_dispatch (rollback)

---
## 🧭 Pipeline Stages
 [deploy.yml](../.github/workflows/deploy.yml)
### 1. Build Application (CI)
- The application is built using Maven:
`mvn clean package`
- This generates a `.jar` file used in Docker image creation.

### 2. Docker Build & Push
- Docker image is built using versioning (commit SHA):
`docker build -t emanabosamra/login-app:<commit-id> .`
- Login to Docker Hub:
`docker login`
- Push image to Docker Hub:
`docker push emanabosamra/login-app:<commit-id>`

### 3. Versioning Strategy
- Each build is tagged using:
`github.sha`
- Example:
login-app:041afd71671adabca
login-app:abc123xyz

- ✔ This allows:
-- Tracking each version
-- Safe deployments
-- Easy rollback

### 4. Deployment (CD)
- The pipeline connects to EC2 using SSH:
- Pulls the latest or selected image
- Stops and removes old container
- Runs the new container
```bash
docker pull emanabosamra/login-app:<tag>
docker rm -f login-app || true
docker run -d -p 8081:8080 --name login-app emanabosamra/login-app:<tag>
```

### 5. Rollback Mechanism 🔥
- Manual rollback using GitHub Actions
- Trigger:
Run workflow → Enter image_tag
- Example:
latest or 041afd71671adabca
- ✔ The pipeline will:
-- Pull selected version
-- Redeploy application
-- Replace current running version

![Rollback](https://github.com/EmanElshahat/DevopsMiniProjects/blob/754a5263ced05a32eaf0221dc32c04c16c061459/P3/screenshots/Screenshot%202026-04-22%20154554.png)

---

## 📂 Workflow File Structure 
```text
.github/
└── workflows/
    └── deploy.yml
```
---
## 🔐 Secrets Configuration
Configured in GitHub:
- `DOCKER_USERNAME`
- `DOCKER_PASSWORD`
- `EC2_HOST`
- `EC2_USER`
- `EC2_KEY`
---

## 🌐 Application Access
The application is accessible via:

`http://51.20.192.103:8081/`

---

## 🚀 Key Features
- ✔ Automated CI/CD pipeline
- ✔ Docker-based deployment
- ✔ Version-controlled releases
- ✔ Manual rollback support
- ✔ Zero-downtime redeployment (basic)
- ✔ Secure deployment using SSH

---

## 🎯 Conclusion
By completing this CI/CD pipeline:

- ✔ The build process is fully automated
- ✔ Docker images are versioned and stored in Docker Hub
- ✔ Deployment to EC2 is automatic after each push
- ✔ Rollback can be performed instantly using GitHub Actions
- ✔ The system is production-ready and scalable

This project represents a real-world DevOps workflow and a strong foundation for advanced topics like Kubernetes, Terraform, and monitoring systems.

