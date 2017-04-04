FROM            hwdm/apbase:35e
MAINTAINER      Howard Mei      <howardleomei@gmail.com>

ENV 			S6_BEHAVIOUR_IF_STAGE2_FAILS=2 \
				S6_KILL_FINISH_MAXTIME=3000 \
				S6_KILL_GRACETIME=1000 \
				LANG=en_US.UTF-8 \
				LC_ALL=en_US.UTF-8 \
				LANGUAGE=en_US.UTF-8 \
				TERM=xterm

ENV 			S6OVERLAY_VERSION=v1.19.1.1
ENV 			GODNSMASQ_VERSION=1.0.7

# Set Default User and Home Dir
USER            root
COPY			etc				/etc
COPY			usr				/usr

# ADD a remote file will commit a new layer, so don't use it for temporary files, unless it's as tiny as ${S6SCRIPTS_VERSION}.tar.gz (7.6KB)
ADD             https://github.com/janeczku/go-dnsmasq/releases/download/${GODNSMASQ_VERSION}/go-dnsmasq-min_linux-amd64        /bin/go-dnsmasq
ADD             https://github.com/just-containers/s6-overlay/releases/download/${S6OVERLAY_VERSION}/s6-overlay-amd64.tar.gz   /tmp/s6-overlay-amd64.tar.gz

# In alpine, more than 3 hundred packages depend on libressl-libcrypto@libressl other than libcrypto@openssl, so we choose libressl as well.
RUN 			apk-install libressl ca-certificates bind-tools curl execline && chmod a+x /bin/go-dnsmasq && \
				tar zxvf /tmp/s6-overlay-amd64.tar.gz --strip-components=1 -C / && rm -f /tmp/s6-overlay-amd64.tar.gz && \
				chmod 0755 /init /usr/bin/s6-service && ln -sf /bin/execlineb /usr/bin/execlineb && \
				apk-cleanup && addgroup go-dnsmasq && adduser -D -g "GO-DNSMASQ Daemon" -s /bin/sh -G go-dnsmasq go-dnsmasq && \
				setcap CAP_NET_BIND_SERVICE=+eip /bin/go-dnsmasq

# Set up a standard volume for logs.
VOLUME 			["/var/log/services"]

# Define the Entry Point and/or Default Command
ENTRYPOINT      ["/init"]

EXPOSE 			53 53/udp
