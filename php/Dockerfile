FROM resin/rpi-raspbian:jessie

# install deps
RUN apt-get update && \
    apt-get install -y php5-mysql php5-fpm \
    && rm -rf /var/lib/apt/lists/*

RUN sed -i 's/^listen = .*/listen = 9000/g' /etc/php5/fpm/pool.d/www.conf

EXPOSE 9000

CMD php5-fpm --force-stderr --nodaemonize --fpm-config /etc/php5/fpm/php-fpm.conf
