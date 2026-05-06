# 🌐 Frontend Setup & Deployment Guide (React)

This document provides a complete guide to set up, build, deploy, and containerize the React frontend application.

---

## 🚀 1. Prerequisites

Ensure the following tools are installed on your system:

- Node.js (v16 or higher recommended)
- npm (comes with Node.js)
- Git (optional but recommended)

---

## 📦 Install Node.js & npm (Linux)
```
sudo apt update
sudo apt install nodejs npm -y
```
---

## ✅ Verify Installation
```
node -v
npm -v
```
---

## 📥 2. Clone the Repository (Optional)
```
git clone <your-repo-url>
cd frontend
```
---

## 📦 3. Install Dependencies
```
npm install
```
---

## ⚙️ 4. Configure Environment Variables
```
vim .env
```
---
```
VITE_API_URL="http://<BACKEND_PUBLIC_IP>:8080/api"
```
---

## 🏗️ 5. Run Application (Development Mode)
```
npm run dev
```
http://localhost:5173

---

## 🏗️ 6. Build for Production
```
npm run build
```
---

## 🌐 7. Deploy Using Apache Server
```
sudo apt install apache2 -y
sudo systemctl start apache2
sudo cp -rf dist/* /var/www/html/
```
---

## 🔐 8. Enable HTTPS
```
sudo apt install certbot python3-certbot-apache -y
sudo certbot --apache
```
---

## 🐳 9. Docker Setup
```
# Build Stage
FROM node:18-alpine AS build
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build

# Production Stage
FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```
---

## ▶️ Run Docker
```
docker build -t react-frontend .
docker run -d -p 80:80 react-frontend
```
---

## 🎯 Summary

- npm install  
- npm run dev  
- npm run build  
- Deploy Apache / Docker  
