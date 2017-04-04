FROM            hwdm/aps6consul:075
MAINTAINER      Howard Mei      <howardleomei@gmail.com>

ENV 			CONSUL_TEMPLATE_VERSION=0.18.1
ENV    			CONSUL_CONFIG_DIR=/etc/consul/conf.d

# Add the files
ADD 			etc 			/etc
ADD				usr				/usr

# Download and install Consul Template
RUN 			apk-install curl && \
				curl -sLo /tmp/consul-template.zip https://releases.hashicorp.com/consul-template/${CONSUL_TEMPLATE_VERSION}/consul-template_${CONSUL_TEMPLATE_VERSION}_linux_amd64.zip && \
				unzip -d /usr/sbin/ /tmp/consul-template.zip && rm -f /tmp/consul-template.zip && \
				apk-remove curl && \
				addgroup consul-template && \
				adduser -D -g "" -s /bin/sh -G consul-template consul-template && \
				addgroup s6 && \
				addgroup consul s6 && \
				addgroup consul-template s6

# For `s6-svc -h` to work properly we want to set proper group permissions
# see: https://github.com/just-containers/s6-overlay/issues/130#issuecomment-181956795
# Also fix permissions
RUN 			mkdir /etc/services.d/consul-template/supervise/ && \
				mkfifo /etc/services.d/consul-template/supervise/control && \
				chown -R root:s6 /etc/services.d/consul-template && \
				chmod g+w /etc/services.d/consul-template/supervise/control /etc/services.d/consul-template
