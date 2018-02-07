FROM php:7.1-fpm
MAINTAINER goozp "gzp@goozp.com"

# set timezome
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Install env
ADD sources.list /etc/apt/sources.list
RUN apt-get update && apt-get install -y \
        git \
        libmemcached-dev \
        libmcrypt-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng12-dev \
        && rm -r /var/lib/apt/lists/*

# Install PHP extensions
COPY ./pkg/redis.tgz /home/redis.tgz
COPY ./pkg/cphalcon.tar.gz /home/cphalcon.tar.gz

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
        && docker-php-ext-install zip \
        && docker-php-ext-install gd \
        && docker-php-ext-install mcrypt \
        && docker-php-ext-install pdo_mysql \
        && docker-php-ext-install opcache \
        && docker-php-ext-install mysqli
RUN pecl install /home/redis.tgz && echo "extension=redis.so" > /usr/local/etc/php/conf.d/redis.ini
RUN cd /home \
    && tar -zxvf cphalcon.tar.gz \
    && mv cphalcon-* phalcon \
    && cd phalcon/build \
    && ./install \
    && echo "extension=phalcon.so" > /usr/local/etc/php/conf.d/phalcon.ini

RUN rm -f /home/redis.tgz \
        rm -f /home/cphalcon.tar.gz 

WORKDIR /data

# Write Permission
RUN usermod -u 1000 www-data
