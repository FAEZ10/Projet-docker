FROM alpine:3.17

# Installation PostgreSQL
RUN apk update && apk add --no-cache postgresql postgresql-contrib

# Création d'un utilisateur non privilégié pour exécuter PostgreSQL
RUN addgroup -S mypostgres && adduser -S -G mypostgres mypostgres

# Attribution des droits appropriés sur le répertoire de données
RUN mkdir -p /var/lib/postgresql/data && chown -R postgres:postgres /var/lib/postgresql/data

# Définir les variables d'environnement pour PostgreSQL
ENV PGDATA=/var/lib/postgresql/data
ENV POSTGRES_USER=myuser
ENV POSTGRES_PASSWORD=mypassword

# Exposer le port PostgreSQL (par défaut : 5432)
EXPOSE 5432

# Commande par défaut pour démarrer PostgreSQL
USER postgres
CMD ["postgres"]
