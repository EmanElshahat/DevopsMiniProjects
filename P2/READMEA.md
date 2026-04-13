# 🚀 Deploy Java Login Application on AWS using Docker & RDS

## 📌 Project Overview
This project demonstrates how to containerize a Spring Boot Java web application using Docker, push the image to Docker Hub, and deploy it on an AWS EC2 instance.
The application is connected to an AWS RDS MySQL database hosted in a private subnet, and exposed to the internet using EC2 public IP and security group configuration.

---

## 🛠️ Tools Used
Spring Boot (Java)
Docker
Docker Hub
AWS EC2
AWS RDS (MySQL)
AWS VPC
Security Groups
Ubuntu Linux

---

## 🧭 Steps
### ☕ Java Application
The application is a Spring Boot web application that provides a login functionality.
It connects to a MySQL database to validate user credentials.
The application runs on:
Port 8081

### 🐳 Docker Containerization
The application was containerized using Docker to create a portable and production-ready image.
Dockerfile was created to package the '.jar' file and run the application.

### 🧭 Docker Commands Used
🔹 Build Docker Image
```bash
docker build -t login-app .
```
🔹 Tag Image for Docker Hub
```bash
docker tag login-app emanabosamra/login-app
```
🔹 Push Image to Docker Hub
```bash
docker push emanabosamra/login-app
```
🔹 Run Container Locally
```bash
docker run -d -p 8080:8080 login-app
```

### ☁️ AWS Deployment
-  Created VPC with Public & Private Subnets
-  Created Internet Gateway & NAT Gateway
-  Created Security Groups
-  Launched EC2 Ubuntu Instance
-  Installed Docker on EC2
-  Pulled Docker Image from Docker Hub
-  Run Container on EC2

### 🗄️ RDS Configuration
- Created MySQL RDS instance in Private Subnet
- Disabled Public Access
- Configured DB Subnet Group
  ![create](https://github.com/EmanElshahat/DevopsMiniProjects/blob/bced8664f7543d44098cc3efae3b759ed5d612df/P2/screenshots/1.png)

- Connected EC2 to RDS via Security Groups
![create](https://github.com/EmanElshahat/DevopsMiniProjects/blob/bced8664f7543d44098cc3efae3b759ed5d612df/P2/screenshots/2.png)

- Created Database manually:
```bash
CREATE DATABASE UserDB;
```

-🔹 Created Table:
```bash
CREATE TABLE users (
id INT AUTO_INCREMENT PRIMARY KEY,
username VARCHAR(50),
password VARCHAR(50)
);
```
-🔹 Inserted Test User:

```bash
INSERT INTO users (username, password) VALUES ('eman', '1234');
```
![create](https://github.com/EmanElshahat/DevopsMiniProjects/blob/bced8664f7543d44098cc3efae3b759ed5d612df/P2/screenshots/3.png)


### 🔗 Application Configuration
Updated application.properties:
```bash
spring.datasource.url=jdbc:mysql:Endpoint//:3306/UserDB
spring.datasource.username=admin
spring.datasource.password=Admin12345
```

### 🌐 Access Application
The application is accessible via:
`http://51.20.192.103:8081/`

 --- 

 ## 🚀 Conclusion
 By completing this project:

✔ The Java application was containerized using Docker
✔ The Docker image was pushed to Docker Hub
✔ The application was deployed on AWS EC2
✔ A secure RDS database was created in a private subnet
✔ EC2 was successfully connected to RDS
✔ The application was exposed to the internet
