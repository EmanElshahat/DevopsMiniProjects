# 🚀 Expose Flask Application on AWS using Docker

## 📌 Project Overview
This project demonstrates how to containerize a Flask application using Docker, push the image to Docker Hub, and deploy it on an AWS EC2 instance. The application is then exposed to the internet using EC2 public IP and security group configuration.

---

## 🛠️ Tools Used
- Flask
- Docker
- Docker Hub
- AWS EC2
- AWS VPC
- Security Groups
- Ubuntu Linux
---

## 🧭 Steps
### 🐍 Flask Application
The Flask application is a simple web server that returns a basic response when accessed from the browser.
The application runs on:
```bash
Port 5000
```
---
### 🐳 Docker Containerization
The application was containerized using Docker with a **multi-stage** build to create a lightweight and production-ready image.
-  [Dockerfile](./App/Dockerfile)

### 🧭 Docker Commands Used
#### Build Docker Image
```bash
docker build -t app .
```
![Build](https://github.com/EmanElshahat/DevopsMiniProjects/blob/57411e936e79441d40273ace425ec65d46025216/P1/screenshots/1.png)

#### Tag Image for Docker Hub $ Push into Docker Hub
```bash
docker tag app <emanabosamra>/flaskapp
docker push <emanabosamra>/flaskapp
```
![Tag](https://github.com/EmanElshahat/DevopsMiniProjects/blob/57411e936e79441d40273ace425ec65d46025216/P1/screenshots/2.png)

#### Run Container Locally
```bash
docker run -d -p 5000:5000 app
```
![Run](https://github.com/EmanElshahat/DevopsMiniProjects/blob/57411e936e79441d40273ace425ec65d46025216/P1/screenshots/3.png)

---
### ☁️ AWS Deployment 
The application was deployed on an AWS EC2 instance with the following steps:
1. Created VPC and Public Subnet

![VPC](https://github.com/EmanElshahat/DevopsMiniProjects/blob/57411e936e79441d40273ace425ec65d46025216/P1/screenshots/4.png)

---
2. Created Security Group (Ports 22, 80, 5000)

![Security](https://github.com/EmanElshahat/DevopsMiniProjects/blob/57411e936e79441d40273ace425ec65d46025216/P1/screenshots/5.png)

---
3. Launched EC2 Ubuntu Instance

![EC2](https://github.com/EmanElshahat/DevopsMiniProjects/blob/57411e936e79441d40273ace425ec65d46025216/P1/screenshots/6.png)

---
4. Connected via SSH

![SSH](https://github.com/EmanElshahat/DevopsMiniProjects/blob/57411e936e79441d40273ace425ec65d46025216/P1/screenshots/7.png)

---
5. Installed Docker on EC2
```bash
sudo apt update
sudo apt install docker.io -y
```
---
6. Pulled Docker image from Docker Hub
7. Run the container and mapped ports

![Pulled](https://github.com/EmanElshahat/DevopsMiniProjects/blob/57411e936e79441d40273ace425ec65d46025216/P1/screenshots/8.png)

---
8. Exposed the application to the internet via Public IP

```bash
http://51.20.192.103
```
![application](https://github.com/EmanElshahat/DevopsMiniProjects/blob/57411e936e79441d40273ace425ec65d46025216/P1/screenshots/9.png)

---

## 🚀 Conclusion
By completing this project:

- The Flask application was containerized using Docker.
- The Docker image was pushed to Docker Hub.
- The application was deployed on AWS EC2.
- The container was run on the cloud server.
- The application was successfully exposed to the internet.

This project represents a basic DevOps deployment workflow and serves as a foundation for future projects involving CI/CD, Terraform, Kubernetes, and cloud automation

