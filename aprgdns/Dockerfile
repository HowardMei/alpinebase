FROM            hwdm/apbase:35e
MAINTAINER      Howard Mei      <howardleomei@gmail.com>

ENV 			GODNSMASQ_VERSION=1.0.7

ADD             https://github.com/janeczku/go-dnsmasq/releases/download/${GODNSMASQ_VERSION}/go-dnsmasq-min_linux-amd64   /bin/go-dnsmasq

COPY				etc			/etc
COPY				usr			/usr
COPY				entrypoint  /entrypoint
	

RUN 			apk-install libressl ca-certificates bind-tools curl runit rsyslog logrotate && \
				chmod a+x /bin/go-dnsmasq && addgroup go-dnsmasq && adduser -D -g "GO-DNSMASQ Daemon" -s /bin/sh -G go-dnsmasq go-dnsmasq && \
				setcap CAP_NET_BIND_SERVICE=+eip /bin/go-dnsmasq && \
				apk-cleanup
