ARG ALPINE_VERSION=3.17
FROM alpine:${ALPINE_VERSION}

RUN apk --no-cache add \
    curl \
    nginx \
    php81 \
    php81-ctype \
    php81-curl \
    php81-dom \
    php81-fpm \
    php81-gd \
    php81-intl \
    php81-mbstring \
    php81-mysqli \
    php81-opcache \
    php81-openssl \
    php81-phar \
    php81-session \
    php81-xml \
    php81-xmlreader \
    supervisor \
    postgresql



# Configuration des fichiers de services
COPY config/nginx.conf /etc/nginx/nginx.conf
COPY config/conf.d /etc/nginx/conf.d/
COPY config/php.ini /etc/php7/conf.d/custom.ini
COPY config/supervisord.conf /etc/supervisor/conf.d/supervisord.conf
COPY config/fpm-pool.conf /etc/php7/php-fpm.d/www.conf
COPY config/postgresql.conf /etc/postgresql.conf 

# Configuration du répertoire racine
WORKDIR /var/www/html

# Ajout de l'application
COPY src/ ./

# Exposition du port sur lequel nginx est accessible
EXPOSE 8000

# Démarrage de supervisord et php-fpm
CMD ["supervisord", "-c", "/etc/supervisord.conf"]
