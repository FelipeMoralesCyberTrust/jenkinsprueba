FROM php:7.1.17-apache
LABEL maintainer="Jaivic"

RUN apt-get update \
    && apt-get upgrade -y \
    && a2enmod rewrite \
    && apt-get install -y \
        zlib1g-dev \
        libicu-dev \
        libxml2-dev \
        libpq-dev \
        vim

RUN docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
    && docker-php-ext-install pdo pdo_mysql pdo_pgsql zip intl xmlrpc soap opcache \
    && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd

COPY . /var/www/html/
WORKDIR /var/www/html/