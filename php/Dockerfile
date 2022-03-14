FROM php:7.4-fpm

RUN apt-get update && apt-get install -y \
    cron \
    default-mysql-client \
    git \
    gzip \
    libbz2-dev \
    libfreetype6-dev \
    libicu-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libonig-dev \
    libpng-dev \
    libsodium-dev \
    libssh2-1-dev \
    libxslt1-dev \
    libzip-dev \
    lsof \
    procps \
    vim \
    zip

RUN docker-php-ext-configure gd --with-freetype --with-jpeg

RUN docker-php-ext-install \
    bcmath \
    bz2 \
    calendar \
    exif \
    gd \
    gettext \
    intl \
    mbstring \
    mysqli \
    opcache \
    pcntl \
    pdo_mysql \
    soap \
    sockets \
    sodium \
    sysvmsg \
    sysvsem \
    sysvshm \
    xsl \
    zip

RUN pecl install redis \
    && docker-php-ext-enable redis

RUN apt-get install -y libmagickwand-dev \
    && pecl install imagick  \
    && docker-php-ext-enable imagick

RUN curl -sL https://deb.nodesource.com/setup_14.x -o nodesource_setup.sh
RUN bash nodesource_setup.sh
RUN apt-get install nodejs
RUN rm nodesource_setup.sh

RUN npm install -g grunt-cli


COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

COPY config/php.ini /usr/local/etc/php/


WORKDIR /var/www/html
