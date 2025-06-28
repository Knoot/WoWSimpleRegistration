FROM php:8.2-fpm

# Установка зависимостей
RUN apt-get update
RUN apt-get install -y \
    libgmp-dev \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libzip-dev \
    libxml2-dev \
    zlib1g-dev \
    libonig-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) \
    gmp \
    gd \
    zip \
    soap \
    mbstring \
    pdo \
    pdo_mysql

# Установка Composer
RUN curl -sS https://getcomposer.org/installer | php -- \
    --install-dir=/usr/local/bin --filename=composer

# Очистка
RUN apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && docker-php-source delete

WORKDIR /app