FROM php:8.2-fpm

WORKDIR /app

RUN apt-get update \
    && apt-get install -y libmemcached-dev zlib1g-dev libssl-dev
RUN yes '' | pecl install -f memcached-3.2.0 \
  && docker-php-ext-enable memcached
RUN docker-php-ext-install mysqli pdo pdo_mysql
RUN apt-get update -y && apt-get install -y curl && apt-get clean -y
RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug;
