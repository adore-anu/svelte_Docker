# stage 1 - build svelt app
FROM node:12-alpine as svelt-app
RUN mkdir -p /var/www/svelt-app
WORKDIR /var/www/svelt-app
COPY package.json ./
RUN npm install
COPY . ./
RUN npm run build
# /var/www/svelt-app/public

FROM ubuntu:latest as nginx
RUN apt-get update
RUN apt-get install nginx -y
COPY --from=svelt-app /var/www/svelt-app/public /var/www/html/
#/var/www/html serve
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]