FROM nginx:1.12

ADD  nginx.conf      /etc/nginx/nginx.conf
ADD  hostcon/*    /etc/nginx/conf.d/
RUN  mkdir /data
    && mkdir /data/www
    && mkdir /data/log
    && mkdir /data/log/nginx
RUN  chown -R www-data.www-data /data/www /data/log

VOLUME ["/data"]