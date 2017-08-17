# zPhal-dockerfiles
dockerfiles that support zPhal's working environment

## 简介
用docker容器服务的方式搭建zPhal环境，易于维护。

相关版本：
- PHP 7.1.8
- MySQL 5.7
- Nginx 1.12
- Memcached 1.5
- Redis 3.2

PHP 拓展：
- composer
- redis 3.1.3
- memcached 3.0.3
- Phalcon 3.2.2

## 使用
1. 安装Docker，Docker-compose
2. 下载zPhal-dockerfiles
```
git clome git@github.com:ZpGuo/zPhal-dockerfiles.git
 
mv zPhal-dockerfiles zPhal
```
3. 下载需要的拓展包
```
cd zPhal
 
wget https://getcomposer.org/composer.phar -O php/composer.phar  
wget https://pecl.php.net/get/redis-3.1.3.tgz -O php/redis.tgz  
wget https://codeload.github.com/phalcon/cphalcon/tar.gz/v3.2.2 -O php/cphalcon.tar.gz 
wget https://pecl.php.net/get/memcached-3.0.3.tgz -O php/memcached.tgz
```

php
build:
docker build -t zphal-php ./php

run:
docker run -d -p 9000:9000 --name php  -v /data/www:/data/www -it zphal-php

nginx
docker build -t zphal-nginx ./nginx

docker run -p 80:80 -v /data/www:/data/www  -it zphal-nginx
