FROM php:7.0

RUN apt-get update && \
    apt-get install -y sendmail && \
    apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libmcrypt-dev mcrypt libxml2-dev libxslt-dev libicu-dev xml-core mysql-client unzip && \
    docker-php-ext-install -j$(nproc) iconv mcrypt && \
    docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
    docker-php-ext-install -j$(nproc) gd && \
    docker-php-ext-install -j$(nproc) mysqli pdo pdo_mysql bcmath xml xsl intl soap && \
    echo 'sendmail_path = "/usr/sbin/sendmail -t -i"' > /usr/local/etc/php/php.ini

CMD ["echo", "'Done'"]