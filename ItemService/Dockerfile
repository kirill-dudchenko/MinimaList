# Use PHP 7.4 FPM as a base image
FROM php:7.4-fpm

# Install system dependencies and PHP extensions
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    && docker-php-ext-install gd

# Set working directory
WORKDIR /var/www

# Copy existing application directory
COPY . .

# Expose port 9000 to interact with the app
EXPOSE 9000
