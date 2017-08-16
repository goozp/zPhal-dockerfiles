FROM nginx:1.12

ADD  nginx.conf      /etc/nginx/nginx.conf
ADD  hostcon/*    /etc/nginx/conf.d/
RUN  mkdir /opt/www && mkdir /opt/log && mkdir /opt/log/nginx
RUN  chown -R www-data.www-data /opt/www /opt/log

VOLUME ["/opt"]