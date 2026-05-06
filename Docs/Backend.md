# ⚙️ Backend Deployment Guide (Spring Boot)

This document provides step-by-step instructions to build, deploy, and containerize a Spring Boot backend application.

---

## 🚀 Prerequisites

Ensure the following are installed:

- Java Development Kit (JDK 17 or higher)
- Maven
- Git (optional)
- Docker (for containerization)

---

## ☕ Step 1: Install Java
```
java -version
```
---
```
sudo apt update
sudo apt install openjdk-17-jdk -y
```
---

## 📦 Step 2: Install Maven
```
sudo apt install maven -y
mvn -version
```
---

## 📥 Step 3: Clone Project (Optional)
```
git clone <your-repo-url>
cd backend
```
---

## ⚙️ Step 4: Configure Database

vim src/main/resources/application.properties

server.port=8080
spring.datasource.url=jdbc:mariadb://<DB_HOST>:3306/<DB_NAME>
spring.datasource.username=<DB_USER>
spring.datasource.password=<DB_PASS>

---

## 🏗️ Step 5: Build Application
```
mvn clean package
```
---

## ▶️ Step 6: Run Application
```
java -jar target/spring-backend-v1.jar
```
---

## 🌐 Access Application
```
http://localhost:8080
```
---

## 🔄 Step 7: Run in Background
```
nohup java -jar target/spring-backend-v1.jar > app.log 2>&1 &
tail -f app.log
```
---

# 🐳 Docker Setup (Backend)

## 📦 Dockerfile
```
FROM openjdk:17-jdk-slim
WORKDIR /app
COPY target/spring-backend-v1.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","app.jar"]
```
---

## ▶️ Build Docker Image
```
docker build -t spring-backend .
```
---

## 🚀 Run Container
```
docker run -d -p 8080:8080 spring-backend
```
---


---



