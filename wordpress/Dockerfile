FROM resin/rpi-raspbian:jessie
MAINTAINER Justin Garrison <justinleegarrison@gmail.com>

# install deps
RUN apt-get update && \
    apt-get install -y php5-mysql php5-fpm curl \
    && rm -rf /var/lib/apt/lists/*

# download caddy
RUN mkdir -p /srv/wordpress && \
    curl -sL  https://github.com/mholt/caddy/releases/download/v0.9.1/caddy_linux_arm7.tar.gz | \
    tar xz -C /tmp/ && mv /tmp/caddy_linux_arm7 /usr/local/bin/caddy && \
    chmod +x /usr/local/bin/caddy

ADD Caddyfile /srv/

# download wordpress
RUN curl -sL http://wordpress.org/latest.tar.gz | \
    tar --strip 1 -xz -C /srv/wordpress

EXPOSE 80 443

WORKDIR /srv

CMD service php5-fpm start && caddy
