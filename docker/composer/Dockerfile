FROM php:7.3-fpm

RUN apt-get update && apt-get install -y libmcrypt-dev \
    mariadb-client libmagickwand-dev --no-install-recommends \
    && pecl install imagick \
    && docker-php-ext-enable imagick \
    && pecl install mcrypt-1.0.3 \
    && docker-php-ext-enable mcrypt \
    && docker-php-ext-install pdo_mysql

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

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN composer self-update 1.10.21

WORKDIR /var/www/html/magento
