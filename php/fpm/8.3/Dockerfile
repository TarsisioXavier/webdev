FROM php:8.3-fpm-alpine

USER root

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/

RUN apk --no-cache --update add git \
    bash \
    bash-completion \
    php83-pecl-redis \
    libmemcached-dev \
    zlib-dev \
    libpng-dev \
    libjpeg-turbo-dev \
    freetype-dev \
    libxml2-dev \
    libzip-dev \
    zip \
    icu-dev

RUN echo "extension=redis.so" >> /etc/php83/php.ini

RUN docker-php-ext-configure intl
RUN docker-php-ext-configure gd --with-freetype --with-jpeg
RUN docker-php-ext-configure zip

RUN docker-php-ext-install \
    gd \
    fileinfo \
    dom \
    xml \
    simplexml \
    pcntl \
    mysqli \
    pdo_mysql \
    intl \
    gd \
    zip

RUN install-php-extensions \
    redis-stable \
    imagick

RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

RUN deluser www-data \
    && addgroup -g 1000 www-data && adduser -u 1000 -G www-data -D -H www-data

WORKDIR /var/www

USER www-data
