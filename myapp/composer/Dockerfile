FROM alpine:3.17

# Mise à jour des référentiels de packages
RUN apk update
#  les dépendances nécessaires
RUN apk update && apk --no-cache add \
    curl \
    git \
    openssh \
    mercurial \
    subversion \
    tini

#  PHP et les extensions requises
RUN apk --no-cache add \
    php81 \
    php81-json \
    php81-openssl \
    php81-phar \
    php81-iconv \
    php81-mbstring \
    php81-pdo \
    php81-pdo_pgsql

# Installation de Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Répertoire de travail
WORKDIR /php

# Copie du fichier composer.json 
COPY dependencies/composer.json dependencies/composer.lock /php/

#  Composer pour installer les dépendances
RUN composer install --no-scripts --no-autoloader --no-dev --prefer-dist

# Copie du code source

# Scripts d'installation et de lancement de l'application
RUN composer dump-autoload --optimize --classmap-authoritative

#EXPOSE 8000


