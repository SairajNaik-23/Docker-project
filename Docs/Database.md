# 🗄️ MariaDB Setup & Configuration Guide

This guide explains how to install MariaDB, secure it, create a database, configure a user, and connect using AWS RDS.

---

## 🚀 1. Install MariaDB (Ubuntu)
```
sudo apt update
sudo apt install mariadb-server -y
```
---

## 🔐 2. Secure MariaDB Installation
```
mysql_secure_installation
```
- Set root password
- Remove anonymous users
- Disable remote root login
- Remove test database

---

## 🧑‍💻 3. Login to MariaDB
```
mysql -u root -p
```
---

## 🗃️ 4. Create Database & User
```
CREATE DATABASE student_db;

GRANT ALL PRIVILEGES ON student_db.* TO 'username'@'localhost' IDENTIFIED BY 'your_password';

FLUSH PRIVILEGES;
```
---

## 🔑 5. Database Credentials

DB_HOST=localhost
DB_USER=username
DB_PASS=your_password
DB_PORT=3306
DB_NAME=student_db

---

## 📊 6. Create Table
```
USE student_db;
```

---
```
CREATE TABLE students (
  id BIGINT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255),
  email VARCHAR(255),
  course VARCHAR(255),
  student_class VARCHAR(255),
  percentage DOUBLE,
  branch VARCHAR(255),
  mobile_number VARCHAR(255)
);
```
---

# ☁️ 7. AWS RDS Setup (Production)
```
## Create RDS
- Engine: MariaDB
- Public access: Yes (for testing)
- Port: 3306
```
## Connect
```
mysql -h <RDS_ENDPOINT> -u admin -p
```
## Create DB
```
CREATE DATABASE student_db;
```
## Update Backend
```
spring.datasource.url=jdbc:mariadb://<RDS_ENDPOINT>:3306/student_db
spring.datasource.username=admin
spring.datasource.password=yourpassword
```
---

## ❌ Exit
```
EXIT;
```
---

## 🧠 Error Handling & Solutions 

| Issue | Solution |
|------|---------|
| Can't login | Check password |
| Access denied | Check privileges |
| RDS not connecting | Check security group |

---

## 🎯 Summary

- Install MariaDB
- Create DB & user
- Create table
- Connect backend
- Use AWS RDS for production

