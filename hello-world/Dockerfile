FROM php:7.4-apache

ENV TZ=Europe/Berlin
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# sudo
RUN echo "php ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php --install-dir=/usr/local/bin/ --filename=composer \
    && php -r "unlink('composer-setup.php');"

RUN docker-php-ext-configure gd --with-freetype --with-jpeg
RUN docker-php-ext-install \
    zip \
    pdo_mysql \
    bcmath \
    intl \
    opcache \
    xml \
    dom \
    simplexml \
    gd \
    soap \
    apcu