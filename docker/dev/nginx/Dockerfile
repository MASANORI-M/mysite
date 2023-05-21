FROM ubuntu:22.04

RUN apt-get update

RUN apt-get install -y nginx

COPY ./default.conf /etc/nginx/conf.d/default.conf
COPY ./nginx.conf /etc/nginx/nginx.conf:cached

ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]