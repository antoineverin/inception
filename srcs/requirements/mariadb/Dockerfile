FROM debian:bullseye

RUN apt update && apt upgrade -y

RUN apt install -y mariadb-server

COPY conf/50-server.cnf /etc/mysql/mariadb.conf.d/50-server.cnf
COPY tools/setup.sh .

RUN chmod u+x ./setup.sh

EXPOSE 3306
VOLUME [ "/var/lib/mysql" ]

CMD [ "./setup.sh" ]
