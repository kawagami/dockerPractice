FROM php:8.1-fpm-alpine

RUN apk add --no-cache nginx wget bash

RUN mkdir -p /run/nginx

COPY docker/nginx.conf /etc/nginx/nginx.conf
COPY docker/startup.sh /app/docker/startup.sh
COPY docker/wait-for-it.sh /app/wait-for-it.sh

WORKDIR /app
COPY ./src /app

RUN sh -c "wget http://getcomposer.org/composer.phar && chmod a+x composer.phar && mv composer.phar /usr/local/bin/composer"
RUN cd /app && \
    /usr/local/bin/composer install --no-dev

# RUN chown -R www-data: /app

RUN chmod -R 777 storage bootstrap/cache


# CMD ["sh", "/app/docker/startup.sh"]
CMD ["sh", "/app/docker/startup.sh"]
