FROM php:8.1-fpm-alpine
COPY . /usr/share/nginx/html/
WORKDIR /usr/share/nginx/html/

COPY --from=composer:2.2.6 /usr/bin/composer /usr/bin/composer
RUN composer install --optimize-autoloader --no-dev

EXPOSE 9000
