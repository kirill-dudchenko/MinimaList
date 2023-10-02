# Use PHP 8.1 FPM as the base image
FROM php:8.1-fpm

# Install system dependencies
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    zip \
    unzip \
    git \
    libzip-dev \
    libonig-dev \
    libxml2-dev

# Install and configure GD
RUN docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd

# Install other PHP extensions
RUN docker-php-ext-install pdo pdo_mysql zip mbstring xml ctype json

# Install Composer globally
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set the working directory
WORKDIR /var/www

# Copy the application files
COPY . .

# Install Composer dependencies
RUN composer install

# Expose port 9000 to interact with the app
EXPOSE 9000
