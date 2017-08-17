# zPhal-dockerfiles
dockerfiles that support zPhal's working environment

简介

```
wget https://getcomposer.org/composer.phar -O php/composer.phar  
wget https://pecl.php.net/get/redis-3.1.3.tgz -O php/redis.tgz  
wget https://codeload.github.com/phalcon/cphalcon/tar.gz/v3.2.2 -O php/cphalcon.tar.gz 
wget https://pecl.php.net/get/memcached-3.0.3.tgz -O php/memcached.tgz
```
进入根目录
cd zphal-dockerfiles

php
build:
docker build -t zphal-php ./php

run:
docker run -d -p 9000:9000 --name php  -v /data/www:/data/www -it zphal-php

nginx
docker build -t zphal-nginx ./nginx

docker run -p 80:80 -v /data/www:/data/www  -it zphal-nginx
