FROM ubuntu:16.04
MAINTAINER tebannew@gmail.com

#Install package
RUN apt-get update -y
RUN apt-get install postgresql -y

#Configuracion del puerto de postgres
EXPOSE 5432
CMD postgresql -m http.server 5432

# Cambia al usuario postgres
USER postgres

# Inicia postgresql, crea usuario (carlos), crea base de datos (prueba) y asigna un propietario
# a la base de datos
RUN    /etc/init.d/postgresql start &&\
psql --command "CREATE USER carlos WITH SUPERUSER PASSWORD 'carlos';" &&\
createdb -O carlos prueba

# Configuracion para conexiones remotas
RUN echo "host all  all    0.0.0.0/0  md5" >> /etc/postgresql/9.5/main/pg_hba.conf
RUN echo "listen_addresses='*'" >> /etc/postgresql/9.5/main/postgresql.conf

# inicio del servicio una vez se inicie el contenedor
ENTRYPOINT /etc/init.d/postgresql start && /bin/bash
