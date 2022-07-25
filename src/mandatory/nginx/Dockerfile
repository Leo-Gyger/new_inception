FROM alpine:3.14
RUN apk update ; apk upgrade ; apk add nginx
RUN apk add openssl
RUN mkdir -p /etc/nginx/ssl
RUN openssl req -newkey rsa:4096 -days 365 -nodes -x509 \
	-subj "/C=CH/ST=VD/L=Local/O=42/OU=lgyger/CN=lgyger" \
	-out /etc/nginx/ssl/ca.pem \
	-keyout /etc/nginx/ssl/ca.key
COPY ./configs/test.conf	/etc/nginx/nginx.conf
COPY ./ressources/index.html	/www/index.html
ENTRYPOINT	[ "nginx", "-g", "daemon off;"]
