# 🎓 Student Management System (Full Stack)

A modern full-stack web application to manage student records using CRUD operations, REST APIs, and containerized deployment.

---

## 🚀 Tech Stack

- 🌐 Frontend: React (Vite)
- ⚙️ Backend: Spring Boot (REST API)
- 🗄️ Database: MariaDB / AWS RDS
- 🚀 Deployment: Docker, Apache, AWS

---

## 📌 Features

- 📝 Add Student
- 📊 View Students (Table)
- ❌ Delete Student
- 🎨 Clean Dark UI
- 🔗 REST API Integration
- 🐳 Docker Support

---

## 🏗️ Architecture

- React (Frontend)
-  ↓
- Spring Boot (Backend)
-  ↓
- MariaDB / AWS RDS

----

## 📂 Project Structure

- student-management-system/
- │
- ├── frontend/
- ├── backend/
- ├── docs/
- ├── docker-compose.yml
- └── README.md

----

## 📖 Documentation

- Frontend → docs/frontend.md  
- Backend → docs/backend.md  
- Database → docs/database.md  

---

## 🖼️ Preview

<p align="center">
  <img src="C:\Users\saira\OneDrive\Pictures\Screenshots 1\Screenshot 2026-04-10 190820.png" width="900" alt="App Preview">
</p>

---

## 📦 Prerequisites

- Node.js & npm
- Java JDK 17+
- Maven
- MariaDB
- Docker (optional)

---

### ⚙️ Manual Setup Login to RDS

```bash
mysql -h <rds-endpoint> -u admin -p
```

### Create Database

```sql
CREATE DATABASE student_db;
```

```sql
USE student_db;
```

### Create Students Table

```sql
CREATE TABLE students (
id bigint NOT NULL AUTO_INCREMENT,
name varchar(255),
email varchar(255),
course varchar(255),
student_class varchar(255),
percentage double,
branch varchar(255),
mobile_number varchar(255),
PRIMARY KEY (id)
);
```

### Exit MySQL

```bash
exit
```
### Configure Database Connection

Edit file:

```bash
nano src/main/resources/application.properties
```

### Build Docker image and push to dockerhub 

````
docker build -t sairaj09/backend .
````
````
docker push sairaj09/backend
````

### Create Backend COntainer
````
docker run -itd --name backend -p 8080:8080 sairaj09/backend
````
### COnfigure Backend Frontend Connection

- edit file
````
nano .env
````
- add instance ip addresss

### Build Docker image and push to dockerhub 

````
docker build -t sairaj09frontend .
````
````
docker push asairaj09/frontend
````

### Create Backend COntainer
````
docker run -itd --name frontend -p 80:80 sairaj09/frontend
````

### Final Result

<img width="1867" height="923" alt="image" src="https://github.com/user-attachments/assets/4287e8e8-3518-42f6-9cf2-750434309ba3" />
