FROM php:8.3-fpm

WORKDIR /app

RUN apt-get update \
    && apt-get install -y libmemcached-dev zlib1g-dev libpng-dev libssl-dev curl \
    && yes '' | pecl install memcached xdebug \
    && docker-php-ext-enable memcached xdebug \
    && docker-php-ext-install mysqli pdo pdo_mysql sockets

ARG UNAME=docker
ARG GID=1000
ARG UID=1000
RUN groupadd -g $GID dockergroup && \
    useradd -m -u $UID -g $GID -s /bin/bash $UNAME

USER $UNAME
