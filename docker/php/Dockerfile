FROM php:7.3-apache

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev

RUN docker-php-ext-configure gd --with-jpeg-dir=DIR \
    && docker-php-ext-install -j$(nproc) gd

RUN apt-get install -y \
    libxml2-dev \
    zlib1g-dev \
    libicu-dev g++

RUN docker-php-ext-configure intl \
    && docker-php-ext-install intl

RUN docker-php-ext-install soap

RUN docker-php-ext-install bcmath

RUN apt-get install -y libxslt-dev

RUN docker-php-ext-install xsl

RUN docker-php-ext-install pdo_mysql

RUN apt-get install -y libzip-dev

RUN docker-php-ext-install zip

RUN docker-php-ext-install sockets

RUN a2enmod rewrite
