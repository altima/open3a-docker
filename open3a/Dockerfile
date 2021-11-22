FROM php:7.2-apache as open3a-base
ENV TZ Europe/Berlin

ADD docker-php-entrypoint /usr/local/bin/
RUN docker-php-ext-install mysqli

ENV DBHOST mariadb
ENV DBUSER open3a
ENV DBPASS open3a
ENV DBNAME open3a

RUN apt update && apt install -y --no-install-recommends unzip

# ###############################################################################
FROM open3a-base

ENV OPEN3A_VERSION 3.5
ADD "https://www.open3a.de/download/open3A%20${OPEN3A_VERSION}.zip" /tmp/open3a_${OPEN3A_VERSION}.zip  
RUN unzip /tmp/open3a_${OPEN3A_VERSION}.zip -d /var/www/html/

RUN mkdir -p /var/www/html/system/session && chmod 0777 /var/www/html/system/session
VOLUME [ "/var/www/html/system/session", "/var/www/html/system/Backup", "/var/www/html/specifics" ]