FROM            hwdm/apbase:35e
MAINTAINER      Howard Mei      <howardleomei@gmail.com>

ENV 			V=2.1.2-r3

COPY				etc			/etc
COPY				usr			/usr
COPY				entrypoint  /entrypoint
	

RUN 			apk-install runit=${V} rsyslog logrotate && \
				apk-cleanup
