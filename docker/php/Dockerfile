FROM php:7.3-apache

RUN apt-get update \
    && apt-get install -y \
        libmcrypt-dev \
        mariadb-client \
        libmagickwand-dev --no-install-recommends \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libxml2-dev \
        zlib1g-dev \
        libicu-dev g++ \
        libxslt-dev \
        libzip-dev \
        unzip \
        cron \
    && pecl install imagick \
    && docker-php-ext-enable imagick \
    && pecl install mcrypt-1.0.3 \
    && docker-php-ext-enable mcrypt \
    && docker-php-ext-install soap \
        bcmath \
        xsl \
        pdo_mysql \
        zip \
        sockets

RUN pecl install xdebug-2.9.8

RUN apt-get install -y libonig-dev

RUN docker-php-ext-configure gd --with-jpeg-dir=DIR --with-freetype-dir=/usr/lib64/ \
    && docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-configure intl \
    && docker-php-ext-install intl

RUN docker-php-ext-install opcache  

RUN a2enmod rewrite

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN composer self-update 1.10.21

RUN apt-get install -y vim

COPY ./php.ini /usr/local/etc/php/conf.d/php.ini
COPY ./xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

RUN chmod 777 /var/www/

USER www-data
