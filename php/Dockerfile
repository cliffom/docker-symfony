FROM ubuntu:15.04
MAINTAINER Michael Clifford <cliffom@gmail.com>

RUN apt-get update && apt-get install -y wget curl php5-common php5-cli php5-fpm php5-mcrypt php5-pgsql php5-curl php5-intl
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN echo 'deb http://apt.newrelic.com/debian/ newrelic non-free' | tee /etc/apt/sources.list.d/newrelic.list
RUN wget -O- https://download.newrelic.com/548C16BF.gpg | apt-key add -
RUN apt-get update && apt-get install -y newrelic-php5 && apt-get clean

ADD symfony.ini /etc/php5/fpm/conf.d/
ADD symfony.ini /etc/php5/cli/conf.d/
ADD newrelic.ini /etc/php5/fpm/conf.d/
ADD newrelic.ini /etc/php5/cli/conf.d/
ADD symfony.pool.conf /etc/php5/fpm/pool.d/

EXPOSE 9000

CMD ["php5-fpm", "-F"]
