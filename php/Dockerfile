FROM php:7.0-fpm
RUN apt-get update && apt-get install -y \
	libfreetype6-dev \
	libjpeg62-turbo-dev \
	libmcrypt-dev \
	libpng-dev \
    curl
RUN docker-php-ext-install \
	zip \
	mcrypt \
	pdo_mysql \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
	&& docker-php-ext-install -j$(nproc) gd
RUN usermod -u 1000 www-data
WORKDIR /var/www/html
CMD ["php-fpm"]
EXPOSE 9000

