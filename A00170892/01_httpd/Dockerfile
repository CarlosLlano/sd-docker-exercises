FROM ubuntu:16.04

RUN \
  apt-get update && \
  apt-get install -y apache2

EXPOSE 80

CMD service apache2 start && tail -f /var/log/apache2/access.log
