FROM php:8.0-fpm-alpine

RUN apk --no-cache update && apk --no-cache add bash \
    && apk add git \
    && apk add --update npm yarn

RUN docker-php-ext-install pdo_mysql

#installer composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php && php -r "unlink('composer-setup.php');" \
    && mv composer.phar /usr/local/bin/composer

# Download and install Symfony CLI
RUN wget https://get.symfony.com/cli/installer -O - | bash

# Add Symfony globally
RUN mv /root/.symfony5/bin/symfony /usr/local/bin/symfony

WORKDIR /var/www/html


