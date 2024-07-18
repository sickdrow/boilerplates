# Use the official PHP image as a base image
FROM php:7.4-apache

# Set environment variables for PrestaShop
ENV PS_VERSION 1.7.8.4
ENV PS_MD5 18d1be1513bb45c9c77edc9bbfeb810b
ENV PS_INSTALL_DIR /var/www/html

# Install required packages and PHP extensions
RUN apt-get update && apt-get install -y \
    wget \
    unzip \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libmcrypt-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd pdo_mysql

# Enable Apache mod_rewrite
RUN a2enmod rewrite

# Download and extract PrestaShop
RUN wget https://download.prestashop.com/download/releases/prestashop_${PS_VERSION}.zip -O prestashop.zip \
    && echo "$PS_MD5 prestashop.zip" | md5sum -c - \
    && unzip prestashop.zip -d $PS_INSTALL_DIR \
    && rm prestashop.zip \
    && chown -R www-data:www-data $PS_INSTALL_DIR

# Set the entrypoint
ENTRYPOINT ["apache2-foreground"]