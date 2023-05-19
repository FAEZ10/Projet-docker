# Dockerfile-adminer
FROM alpine:3.17

# Dépendances PHP et Adminer
RUN apk add --no-cache \
    php \
    php-session \
    php-pdo_pgsql \
    php-pdo \
    php-json \
    php-mbstring \
    php-ctype \
    wget

WORKDIR /var/www

# Installation Adminer
RUN wget -O adminer.php https://github.com/vrana/adminer/releases/download/v4.8.1/adminer-4.8.1-en.php


EXPOSE 8080

CMD /usr/bin/php -S 0.0.0.0:8080

