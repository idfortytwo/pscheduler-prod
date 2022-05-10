FROM nginx:mainline-alpine

RUN rm /etc/nginx/conf.d/*

COPY ./frontend/static /usr/share/nginx/html/
RUN ls /usr/share/nginx/html/

ADD ./frontend/nginx.conf /etc/nginx/conf.d/
