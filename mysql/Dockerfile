FROM mysql:8.0

ENV MYSQL_ROOT_PASSWORD="icaro_password"
ENV MYSQL_DATABASE="gac_database"

VOLUME /var/lib/mysql

COPY config.sql /docker-entrypoint-initdb.d/
COPY create_database.sql /docker-entrypoint-initdb.d/

EXPOSE 3306
