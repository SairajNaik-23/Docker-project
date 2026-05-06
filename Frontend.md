### Edit the .env file 
- Add the EC2 IP
- VITE_API_URL=http://3.110.207.61:8080/api
-----

### Frontend Dockerfile
----
- FROM node:24-alpine
- COPY . /opt/
- WORKDIR /opt
- RUN npm install && npm run build
- RUN apk update && apk add apache2
- RUN rm -rf /var/www/localhost/htdocs/*
- RUN cp -rf dist/* /var/www/localhost/htdocs
- EXPOSE 80
- ENTRYPOINT ["httpd","-D","FOREGROUND"]
----

### Docker frontend-deploy.yml
---
- apiVersion: apps/v1
- kind: Deployment
- metadata: 
-    name: frontend 
-    labels:
-       app: frontend
-  spec:
-  replicas: 3
-  selector:
-    matchLabels:
-      app: frontend
-  template:
-    metadata:
-      name: frontend
-      labels:
-        app: frontend
-   spec:
-     containers:
-         name: frontend
-          image: r123mahajan/frontend:latest
-          ports:
-             containerPort: 80
-----
