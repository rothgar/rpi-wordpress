FROM resin/rpi-raspbian:jessie

# install deps
RUN apt-get update && \
    apt-get install -y curl && \
    rm -rf /var/lib/apt/lists/*

# download caddy
RUN mkdir -p /srv/wordpress && \
    curl -sL  https://github.com/mholt/caddy/releases/download/v0.9.1/caddy_linux_arm7.tar.gz | \
    tar xz -C /tmp/ && mv /tmp/caddy_linux_arm7 /usr/local/bin/caddy && \
    chmod +x /usr/local/bin/caddy

EXPOSE 80 443

WORKDIR /srv

CMD caddy
