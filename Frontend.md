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


