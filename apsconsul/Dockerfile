FROM            hwdm/aps6base:11911e1
MAINTAINER      Howard Mei      <howardleomei@gmail.com>

ENV 			CONSUL_VERSION=0.7.5
ENV 			CONSUL_DOMAIN=consul \
				CONSUL_CONFIG_DIR=/etc/consul/conf.d/bootstrap \
				CONSUL_SERVER_NAME=consul \
				CONSUL_DC=dc1 \
				CONSUL_CLIENT=0.0.0.0 \
				CONSUL_RETRY_INTERVAL=5s

# Add the files
ADD 			etc		/etc
ADD				usr		/usr

# Download and install Consul
RUN 			addgroup consul && adduser -D -g "" -s /bin/sh -G consul consul && apk-install curl && \
				curl -sSLo /tmp/consul.zip https://releases.hashicorp.com/consul/{$CONSUL_VERSION}/consul_${CONSUL_VERSION}_linux_amd64.zip && \
				unzip -d /bin /tmp/consul.zip && rm -f /tmp/consul.zip && apk-remove curl && chmod a+x /usr/bin/consul* && \
				mkdir -p /var/data/consul && chown -R consul:consul /var/data/consul

# Expose the consul data directory as a volume since there's mutable state in there.
VOLUME 			["/var/data/consul"]

# Server RPC is used for communication between Consul clients and servers for internal
# request forwarding.
EXPOSE 			8300

# Serf LAN and WAN (WAN is used only by Consul servers) are used for gossip between
# Consul agents. LAN is within the datacenter and WAN is between just the Consul
# servers in all datacenters.
EXPOSE 			8301 8301/udp 8302 8302/udp

# CLI, HTTP, and DNS (both TCP and UDP) are the primary interfaces that applications
# use to interact with Consul.
EXPOSE 			8400 8500 8600 8600/udp

