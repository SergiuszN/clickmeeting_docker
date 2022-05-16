FROM php:8.1

RUN apt-get -y update --fix-missing
RUN apt-get upgrade -y
RUN apt-get -y install --fix-missing ssl-cert nano wget apt-utils build-essential git curl  libcurl4 \
    libcurl4-openssl-dev zip libwebp-dev libjpeg62-turbo-dev libpng-dev libxpm-dev libfreetype6-dev \
    zlib1g-dev  libsqlite3-dev libsqlite3-0 mariadb-client libzip-dev libicu-dev

# Extensions
RUN pecl install xdebug
RUN pecl install apcu
RUN docker-php-ext-enable xdebug
RUN docker-php-ext-enable apcu

RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install pdo_sqlite
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install curl
RUN docker-php-ext-install zip
RUN docker-php-ext-install intl
RUN docker-php-ext-install bcmath
RUN docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/
RUN docker-php-ext-install gd
RUN docker-php-ext-install opcache

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/html
ADD . /var/www/html

ENTRYPOINT ["tail"]
CMD ["-f","/dev/null"]
