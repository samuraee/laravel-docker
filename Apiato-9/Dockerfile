FROM php:7.4-fpm-alpine

# Install dev dependencies
RUN apk add --no-cache --virtual .build-deps \
    $PHPIZE_DEPS \
    curl-dev \
    imagemagick-dev \
    libtool \
    libxml2-dev \
    postgresql-dev

# Install production dependencies
RUN apk add --no-cache \
    bash \
    curl \
    freetype-dev \
    g++ \
    gcc \
    git \
    icu-dev \
    icu-libs \
    imagemagick \
    libc-dev \
    libjpeg-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
    libzip-dev \
    make \
    mysql-client \
    nodejs \
    nodejs-npm \
    oniguruma-dev \
    openssl \
    yarn \
    openssh-client \
    postgresql-libs \
    rsync \
    tzdata \
    vim \
    yarn \
    zlib-dev

# Install PECL and PEAR extensions
RUN pecl install \
    redis \
    imagick \
    xdebug

# Enable PECL and PEAR extensions
RUN docker-php-ext-enable \
    redis \
    imagick \
    xdebug

# Configure php extensions
RUN docker-php-ext-configure gd --with-freetype --with-jpeg && \
    docker-php-ext-install gd

# Install php extensions
RUN docker-php-ext-install \
    bcmath \
    calendar \
    curl \
    exif \
    gd \
    iconv \
    intl \
    mbstring \
    pdo \
    pdo_mysql \
    pdo_pgsql \
    soap \
    pcntl \
    tokenizer \
    xml \
    zip

# Set container timezone
RUN  cp /usr/share/zoneinfo/Asia/Tehran /etc/localtime \
     && echo "Asia/Tehran" >  /etc/timezone \
     && echo "Asia/Tehran" >  /etc/TZ
ENV TZ=Asia/Tehran


# Install composer
ENV COMPOSER_HOME /composer
ENV PATH ./vendor/bin:/composer/vendor/bin:$PATH
ENV COMPOSER_ALLOW_SUPERUSER 1
RUN curl -s https://getcomposer.org/installer | php -- --1 --install-dir=/usr/local/bin/ --filename=composer

# Install PHP_CodeSniffer
RUN composer global require "squizlabs/php_codesniffer=*"

# Cleanup dev dependencies
RUN apk del -f .build-deps tzdata

# Setup working directory
WORKDIR /var/www
