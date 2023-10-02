# Use PHP 8.1 FPM as a base image
FROM php:8.1-fpm

# Install system dependencies and PHP extensions
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    && docker-php-ext-install gd

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
