# laravel-docker

Sample Usage:

```dockerfile

FROM aboozar/laravel-docker:7.4

LABEL "maintainer"="Aboozar Ghaffari <aboozar.ghf@gmail.com>"

ADD . /var/www/

WORKDIR /var/www

COPY php-upload.www.ini /usr/local/etc/php/conf.d/sarresid-upload.ini
COPY php-fpm.www.ini /usr/local/etc/php-fpm.d/www.conf

RUN composer install --no-dev --no-progress

```
