FROM php:8.0-fpm

RUN apt-get update \
    && apt-get install -y zlib1g-dev g++ git libicu-dev zip libzip-dev libssl-dev libxml2-dev libpq-dev \
    && docker-php-ext-install -j$(nproc) intl opcache pdo pdo_mysql\
    && pecl install apcu \
    && docker-php-ext-enable apcu \
    && docker-php-ext-enable sodium \    
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip \
    && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*


WORKDIR /var/www

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer --quiet

RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN mv /root/.symfony/bin/symfony /usr/local/bin/symfony

RUN git config --global user.email "andreylv0920@gmail.com" && \ 
    git config --global user.name "AndreyLV0920"

EXPOSE 9000    
