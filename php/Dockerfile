FROM php:5.6-apache

RUN a2enmod rewrite

RUN apt-get update && apt-get upgrade -y \
     && apt-get install -y \
         g++ \
         git \
         libfreetype6-dev \
         libicu-dev \
         libjpeg62-turbo-dev \
         libmcrypt-dev \
         libpng12-dev \
         libxml++2.6-dev \
         libxslt-dev \
         unzip \
         wget \
         zlib1g-dev \
     \
     && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
     && docker-php-ext-configure intl \
     \
     && docker-php-ext-install -j$(nproc) gd iconv intl mbstring mcrypt mysqli pdo pdo_mysql soap xml xsl zip \
     \
     && rm -rf /var/lib/apt/lists/*

RUN set -ex \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer