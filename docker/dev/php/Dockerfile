FROM ubuntu:22.04

RUN apt-get update
RUN apt-get install -y vi less php-intl \
    php-cli php-json php-common php-devel php-fpm \
    php-gd php-mysqlnd php-mbstring php-pdo php-xml

# install php8.1
RUN apt-get install -y php8.1 -y

# unix socket
RUN mkdir /var/run/php-fpm
VOLUME [ "/var/run/php-fpm" ]

RUN echo 'short_open_tag = On' >> /etc/php.ini
EXPOSE 9000

# run php-fpm in the foreground
ENTRYPOINT /usr/sbin/php-fpm -F

WORKDIR /var/www/vhosts/mysite

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
COPY ./www.conf /etc/php-fpm.d/www.conf
COPY ./php.ini /etc/php.ini

# nodeのインストール
RUN curl -fsSL https://rpm.nodesource.com/setup_18.x | bash -
RUN apt-get install -y nodejs

# Node.jsの依存パッケージインストール
RUN npm install -g npm