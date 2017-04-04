FROM            hwdm/aps6base
MAINTAINER      Howard Mei      <howardleomei@gmail.com>

ENV				V=7

# Add the files
ADD 			etc 			/etc
ADD 			var 			/var

# Install php, its extensions and composer
RUN 			set -x && apk-install ca-certificates libressl jpegoptim@testing optipng \
					php${V} php${V}-common php${V}-fpm php${V}-opcache php${V}-openssl \
					php${V}-posix php${V}-session php${V}-sockets php${V}-dom php${V}-bcmath php${V}-stats@testing php${V}-tidy \
					php${V}-mbstring php${V}-ctype php${V}-intl php${V}-timezonedb@testing php${V}-iconv \
					php${V}-curl php${V}-ftp php${V}-json php${V}-xml php${V}-xsl php${V}-xmlrpc php${V}-xmlreader \
					php${V}-phar php${V}-gmp php${V}-apcu php${V}-calendar php${V}-zlib php${V}-zip php${V}-bz2 \
					php${V}-mcrypt php${V}-gettext php${V}-exif php${V}-pspell php${V}-enchant \
					php${V}-sysvmsg php${V}-sysvsem php${V}-sysvshm php${V}-shmop php${V}-pcntl \
					php${V}-dba php${V}-pdo php${V}-pdo_dblib php${V}-mysqlnd php${V}-pdo_mysql \
					php${V}-gd php${V}-xdebug && \
					ln -s /etc/php${V} /etc/php && ln -s /var/lib/php${V} /var/lib/php && \
					ln -s /usr/bin/php${V} /bin/php && ln -s /usr/sbin/php-fpm${V} /sbin/php-fpm && \
					chown -R www-data:www-data /var/www /var/run/php /var/log/php && \
					curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer && \
					ln -s /usr/bin/composer /usr/bin/pcos && \
				set +x && apk-cleanup

## Other php extensions: php${V}-pdo_sqlite php${V}-pdo_pgsql 
##		  php${V}-soap php${V}-imap php${V}-ldap php${V}-ssh2@testing php${V}-oauth@testing php${V}-zmq@testing php${V}-msgpack@testing php${V}-snmp 						 
##       php${V}-uuid@testing php${V}-mailparse@testing php${V}-pecl@testing php${V}-redis@testing php${V}-memcached@testing 

# Activate s6-fdholderd by default, or else stage2 might fail during cont-init
RUN 			s6-rmrf /etc/s6/services/s6-fdholderd/down

EXPOSE 			9000
