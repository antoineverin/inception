FROM debian:bullseye

RUN apt update && apt upgrade -y
RUN apt install -y \
	php7.4 \
	php-fpm \
	php-mysql \
	wget

RUN wget https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
	&& chmod +x wp-cli.phar \
	&& mv wp-cli.phar /usr/local/bin/wp

RUN mkdir -p /run/php

COPY conf/www.conf /etc/php/7.4/fpm/pool.d/
COPY tools/setup.sh .

RUN chmod u+x setup.sh

EXPOSE 9000
VOLUME [ "/var/www/html" ]

CMD [ "./setup.sh" ]
