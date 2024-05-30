FROM debian:bullseye

RUN apt update && apt upgrade -y
RUN apt install -y nginx openssl

RUN mkdir /etc/nginx/ssl
RUN openssl req -x509 -nodes \
	-out /etc/nginx/ssl/averin.42.fr.crt \
	-keyout /etc/nginx/ssl/averin.42.fr.key \
	-subj "/C=FR/ST=IDF/L=Paris/O=42/OU=42/CN=averin.42.fr/UID=averin"

# COPY conf/nginx.conf /etc/nginx/nginx.conf

RUN rm -rf /etc/nginx/sites-enabled/default /etc/nginx/sites-available/default
COPY ./conf/averin.42.fr /etc/nginx/sites-available/averin.42.fr
RUN ln -s /etc/nginx/sites-available/averin.42.fr /etc/nginx/sites-enabled/averin.42.fr

RUN ln -sf /dev/stdout /var/log/nginx/access.log \
	&& ln -sf /dev/stderr /var/log/nginx/error.log

EXPOSE 443

CMD [ "nginx", "-g", "daemon off;" ]
