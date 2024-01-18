FROM php:7.1.17-apache
LABEL maintainer="Jaivic"

# Actualizar la lista de paquetes e instalar las herramientas necesarias
RUN apt-get update && apt-get install -y \
    apt-transport-https \
    lsb-release \
    ca-certificates \
    wget

# Agregar el repositorio de Debian
RUN echo "deb http://deb.debian.org/debian $(lsb_release -sc) main" > /etc/apt/sources.list

# Instalar paquetes adicionales
RUN apt-get update && apt-get install -y \
    zlib1g-dev \
    libicu-dev \
    libxml2-dev \
    libpq-dev \
    vim

# Actualizar y mejorar la seguridad
RUN apt-get upgrade -y && apt-get dist-upgrade -y

# Habilitar el módulo de reescritura de Apache
RUN a2enmod rewrite

# Copiar el código fuente de la aplicación
COPY . /var/www/html/
WORKDIR /var/www/html/