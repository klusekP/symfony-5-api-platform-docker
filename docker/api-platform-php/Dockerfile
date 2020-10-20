FROM php:7.4-fpm

RUN apt-get update && apt-get install -y curl git zip libmcrypt-dev mariadb-client

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    composer --version && \
    docker-php-ext-install pdo pdo_mysql && \
    apt-get clean

RUN usermod -u 1000 www-data

WORKDIR /var/www/api-platform
