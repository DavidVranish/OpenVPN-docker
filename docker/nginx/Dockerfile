FROM busybox

RUN apt-get update
RUN apt-get install -y apt-utils

RUN apt-get install -y cron \
    hostname \
    nginx \
    nginx-common \
    nginx-full \
    openssl \
    openssh-server \
    php-common \
    php-curl \
    php-gd \
    php-igbinary \
    php-imap \
    php-mbstring \
    php-memcached \
    php-msgpack \
    php-mysql \
    php-pear \
    php-pgsql \
    php-soap \
    php-sqlite3 \
    php-xdebug \
    php-xml \
    php7.0-bcmath \
    php7.0-cli \
    php7.0-common \
    php7.0-curl \
    php7.0-dev \
    php7.0-fpm \
    php7.0-gd \
    php7.0-imap \
    php7.0-intl \
    php7.0-json \
    php7.0-mbstring \
    php7.0-mcrypt \
    php7.0-mysql \
    php7.0-opcache \
    php7.0-pgsql \
    php7.0-readline \
    php7.0-soap \
    php7.0-sqlite3 \
    php7.0-xml \
    php7.0-zip \
    pkg-php-tools \
    redis-server \
    redis-tools \
    wget \
    composer

RUN composer global require "laravel/installer"
RUN useradd --create-home --shell /bin/bash --groups sudo scs

# Create a random strong password for the user. We don't need to know it
# because we'll be using an SSH key

RUN echo scs:`openssl rand -base64 48` | chpasswd
RUN mkdir /home/scs/.ssh

RUN wget https://dl.eff.org/certbot-auto -O /usr/local/sbin/certbot-auto
RUN chmod a+x /usr/local/sbin/certbot-auto

RUN rm /etc/nginx/sites-enabled/*
RUN rm /etc/nginx/sites-available/*

COPY start /start
4567890
RUN chmod +x /start

RUN mkdir -p /data/www
RUN mkdir -p /etc/letsencrypt
RUN openssl dhparam -out /etc/ssl/certs/dhparam.pem 2048

EXPOSE 22
EXPOSE 80
EXPOSE 443

RUN mkdir /data

CMD /start
