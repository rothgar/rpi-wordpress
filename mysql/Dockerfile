FROM hypriot/rpi-mysql:5.5
MAINTAINER Justin Garrison <justinleegarrison@gmail.com>

# add gosu for easy step-down from root
ENV GOSU_VERSION 1.9
RUN set -x \
	&& apt-get update && apt-get install -y --no-install-recommends ca-certificates wget && rm -rf /var/lib/apt/lists/* \
	&& wget -O /usr/local/bin/gosu "https://github.com/tianon/gosu/releases/download/$GOSU_VERSION/gosu-$(dpkg --print-architecture | awk -F- '{ print $NF }')" \
	&& wget -O /usr/local/bin/gosu.asc "https://github.com/tianon/gosu/releases/download/$GOSU_VERSION/gosu-$(dpkg --print-architecture | awk -F- '{ print $NF }').asc" \
	&& export GNUPGHOME="$(mktemp -d)" \
	&& gpg --keyserver ha.pool.sks-keyservers.net --recv-keys B42F6819007F00F88E364FD4036A9C25BF357DD4 \
	&& gpg --batch --verify /usr/local/bin/gosu.asc /usr/local/bin/gosu \
	&& rm -r "$GNUPGHOME" /usr/local/bin/gosu.asc \
	&& chmod +x /usr/local/bin/gosu \
	&& gosu nobody true \
	&& apt-get purge -y --auto-remove ca-certificates wget \
        && rm -rf /var/lib/apt/lists/*

RUN mkdir /docker-entrypoint-initdb.d

ADD my-small.cnf /etc/mysql/conf.d/
ADD entrypoint.sh /
