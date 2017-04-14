FROM            hwdm/apswpbase
MAINTAINER      Howard Mei      <howardleomei@gmail.com>

ENV				VVV=7

# Add the files
ADD 			etc 			/etc
ADD 			var 			/var

# Install git, wordpress
RUN 			set -x && apk-install git && \

				set +x && apk-cleanup

## Other php extensions: php${V}-pdo_sqlite php${V}-pdo_pgsql 
##		  php${V}-soap php${V}-imap php${V}-ldap php${V}-ssh2@testing php${V}-oauth@testing php${V}-zmq@testing php${V}-msgpack@testing php${V}-snmp 						 
##       php${V}-uuid@testing php${V}-mailparse@testing php${V}-pecl@testing php${V}-redis@testing php${V}-memcached@testing 

# Activate s6-fdholderd by default, or else stage2 might fail during cont-init
RUN 			s6-rmrf /etc/s6/services/s6-fdholderd/down

EXPOSE 			9000
