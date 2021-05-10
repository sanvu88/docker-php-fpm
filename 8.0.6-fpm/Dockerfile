FROM php:8.0.6-fpm

LABEL maintainer="Sanvv - Hostvn Technical <sanvv@hostvn.com>"

RUN apt-get update && apt-get upgrade -y \
    && apt-get install -y \
        g++ \
        libbz2-dev \
        libc-client-dev \
        libcurl4-gnutls-dev \
        libedit-dev \
        libfreetype6-dev \
        libicu-dev \
        libjpeg62-turbo-dev \
        libkrb5-dev \
        libldap2-dev \
        libldb-dev \
        libmagickwand-dev \
        libmcrypt-dev \
        libmemcached-dev \
        libpng-dev \
        libpq-dev \
        libsqlite3-dev \
        libssl-dev \
        libreadline-dev \
        libxslt1-dev \
        libzip-dev \
        wget \
        unzip \
        zlib1g-dev \
    && docker-php-ext-install -j$(nproc) \
        bcmath \
        bz2 \
        calendar \
        exif \
        gettext \
        mysqli \
        opcache \
        pdo_mysql \
        pdo_pgsql \
        soap \
        sockets \
        xsl \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && PHP_OPENSSL=yes docker-php-ext-configure imap --with-kerberos --with-imap-ssl \
    && docker-php-ext-install -j$(nproc) imap \
    && docker-php-ext-configure intl \
    && docker-php-ext-install -j$(nproc) intl \
    && docker-php-ext-configure ldap \
    && docker-php-ext-install ldap \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip \
    && pecl install memcached && docker-php-ext-enable memcached \
    && pecl install mongodb && docker-php-ext-enable mongodb \
    && pecl install redis && docker-php-ext-enable redis

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer
RUN wget https://getcomposer.org/download/1.10.22/composer.phar
RUN mv composer.phar /usr/local/bin/composer1 && chmod +x /usr/local/bin/composer1

RUN docker-php-source delete \
        && apt-get remove -y g++ wget \
        && apt-get autoremove --purge -y && apt-get autoclean -y && apt-get clean -y \
        && rm -rf /var/lib/apt/lists/* \
        && rm -rf /tmp/* /var/tmp/*

RUN touch /usr/local/etc/php/conf.d/opcache-default.blacklist

COPY config/php-fpm.conf /usr/local/etc/
COPY config/php.ini /usr/local/etc/php/
COPY config/00-hostvn-custom.ini /usr/local/etc/php/conf.d
COPY config/docker-php-ext-opcache.ini /usr/local/etc/php/conf.d
COPY config/www.conf /usr/local/etc/php-fpm.d
COPY config/pool.conf.example /usr/local/etc/php-fpm.d
