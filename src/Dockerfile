FROM php:7-apache

RUN mkdir -p /var/www/public && docker-php-ext-install mysqli && docker-php-ext-enable mysqli && mv /usr/local/etc/php/php.ini-production /usr/local/etc/php/php.ini

COPY 000-default.conf /etc/apache2/sites-available/000-default.conf
COPY start-apache /usr/local/bin
RUN a2enmod rewrite

# Copy application source
COPY . /var/www/public
RUN chown -R www-data:www-data /var/www/public

CMD ["start-apache"]
