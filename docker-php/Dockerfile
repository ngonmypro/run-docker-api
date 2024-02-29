FROM public.ecr.aws/docker/library/php:7.4-fpm

# Install package dependencies
RUN apt-get update && apt-get install -y \
    sudo \
    git \
    zip \
    unzip \
    curl \
    libicu-dev \
    libbz2-dev \
    libonig-dev \
    libpng-dev \
    libjpeg-dev \
    libmcrypt-dev \
    libreadline-dev \
    libfreetype6-dev \
    libzip-dev \
    g++ \
    postgresql \
    postgresql-contrib \
    libpq-dev \
  && rm -rf /var/lib/apt/lists/*

# Install Composer
RUN curl -sLS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin/ --filename=composer

# Enable PHP extension
RUN docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/
RUN docker-php-ext-install \
    bcmath \
    bz2 \
    calendar \
    gd \
    intl \
    iconv \
    mbstring \
    opcache \
    pdo \
    pdo_pgsql \
    pgsql \
    zip

RUN pecl install apcu && docker-php-ext-enable apcu