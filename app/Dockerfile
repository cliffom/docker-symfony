FROM ubuntu:15.04
MAINTAINER Michael Clifford <cliffom@gmail.com>

RUN apt-get update && apt-get install -y curl unzip git php5-common php5-cli && apt-get clean
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN mkdir -p /var/www/symfony; chown www-data:www-data /var/www/symfony

USER www-data
COPY app.zip /var/www/symfony

WORKDIR /var/www/symfony
RUN unzip app.zip; rm app.zip;

WORKDIR /var/www/symfony/web

WORKDIR /var/www/symfony
ENV SYMFONY_ENV=prod
RUN composer install --no-dev --optimize-autoloader