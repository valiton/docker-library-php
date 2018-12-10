FROM php:7.0

RUN apt-get update && \
    apt-get install -y sendmail && \
    apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libmcrypt-dev mcrypt libxslt-dev xml-core mysql-client unzip && \
    docker-php-ext-install -j$(nproc) iconv mcrypt && \
    docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
    docker-php-ext-install -j$(nproc) gd && \
    docker-php-ext-install -j$(nproc) mysqli pdo pdo_mysql bcmath xml xsl intl soap && \
    echo 'sendmail_path = "/usr/sbin/sendmail -t -i"' > /usr/local/etc/php/php.ini

RUN apt-get -y update && apt-get -y upgrade && apt-get -y install \
    git autoconf tzdata openntpd libcurl3-dev coreutils \
    libxpm-dev libjpeg-dev libvpx-dev \
    libpng-dev libssl-dev libxml2-dev libicu-dev openssh-client software-properties-common \
    libfontconfig1 libxrender1 libmagickwand-dev

RUN apt-get -y install \
    dpkg-dev dpkg \
    file \
    g++ \
    gcc \
    libc-dev \
    make \
    pkgconf \
    re2c

RUN pecl install xdebug && docker-php-ext-enable xdebug

# Install composer
RUN curl -sS https://getcomposer.org/installer | \
    php -- --install-dir=/usr/local/bin --filename=composer

CMD ["echo", "'Done'"]
