# Use PHP 8.1 FPM as a base image
FROM php:8.1-fpm

# Install system dependencies, PHP extensions, Git, and Unzip
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    git \
    unzip \
    && docker-php-ext-install gd \
    && docker-php-ext-install zip

# Install Composer globally
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set working directory
WORKDIR /var/www

# Copy existing application directory
COPY . .

# Install Composer dependencies
RUN composer install

# Expose port 9000 to interact with the app
EXPOSE 9000
