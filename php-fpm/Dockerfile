FROM debian:jessie

MAINTAINER Vincent Composieux <vincent.composieux@gmail.com>

ADD php.list /etc/apt/sources.list.d/

RUN apt-get update && apt-get install -y wget
RUN wget https://www.dotdeb.org/dotdeb.gpg && apt-key add dotdeb.gpg

RUN apt-get update && apt-get install -y php7.0-cli php7.0-fpm php7.0-mysql php7.0-pgsql php7.0-sqlite php7.0-gd php7.0-curl php7.0-intl php7.0-json

RUN mv /etc/php/7.0/fpm/pool.d/www.conf /etc/php/7.0/fpm/pool.d/00-www.conf
ADD symfony.ini /etc/php/7.0/fpm/conf.d/
ADD symfony.ini /etc/php/7.0/cli/conf.d/

ADD symfony.pool.conf /etc/php/7.0/fpm/pool.d/

RUN usermod -u 1000 www-data

RUN mkdir /run/php && chown www-data /run/php

CMD ["php-fpm7.0", "-F"]

EXPOSE 9000
