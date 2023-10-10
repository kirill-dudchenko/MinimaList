# Use PHP 8.1 FPM as the base image
FROM php:8.1-fpm

# Install system dependencies and PHP extensions
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    zip \
    unzip \
    git \
    libzip-dev \
    libonig-dev \
    libxml2-dev \
    && docker-php-ext-install pdo_mysql zip \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

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
CMD ["php-fpm"]
