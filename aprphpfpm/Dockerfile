FROM            hwdm/aprunit
MAINTAINER      Howard Mei      <howardleomei@gmail.com>

ARG             V=7
ENV             _EXPOSE_TO=9000
ENV             PHP_MEMORY_LIMIT_MB=256
ENV             UPLOAD_MAX_FILE_MB=32
ENV             UPLOAD_MAX_FILENO=20

# Add the files
ADD             etc             /etc
ADD             var             /var

# Install php, its extensions and composer
RUN             set -x && apk-install curl ca-certificates libressl jpegoptim@testing optipng \
                    php${V} php${V}-common php${V}-fpm php${V}-opcache php${V}-openssl \
                    php${V}-posix php${V}-session php${V}-sockets php${V}-dom php${V}-bcmath php${V}-tidy \
                    php${V}-mbstring php${V}-ctype php${V}-intl php${V}-iconv php${V}-imap php${V}-soap php${V}-ldap \
                    php${V}-curl php${V}-ftp php${V}-json php${V}-xml php${V}-xsl php${V}-xmlrpc php${V}-xmlreader \
                    php${V}-phar php${V}-gmp php${V}-apcu php${V}-calendar php${V}-zlib php${V}-zip php${V}-bz2 \
                    php${V}-mcrypt php${V}-gettext php${V}-exif php${V}-pspell php${V}-enchant \
                    php${V}-sysvmsg php${V}-sysvsem php${V}-sysvshm php${V}-shmop php${V}-pcntl \
                    php${V}-dba php${V}-pdo php${V}-pdo_dblib php${V}-pdo_sqlite php${V}-mysqlnd php${V}-pdo_mysql php${V}-pdo_pgsql \
                    php${V}-gd php${V}-xdebug && \
                    ln -s /var/lib/php${V} /var/lib/php && ln -s /usr/bin/php${V} /bin/php && \
                    chown -R www-data:www-data /var/www && chmod a+x /etc/preinit.d/* /etc/postclr.d/* && \
                    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer && \
                    ln -s /usr/bin/composer /usr/bin/pcos && \
                set +x && apk-cleanup

## Other php extensions: php${V}-stats@testing php${V}-timezonedb@testing
##       php${V}-ssh2@testing php${V}-oauth@testing php${V}-zmq@testing php${V}-msgpack@testing php${V}-snmp
##       php${V}-uuid@testing php${V}-mailparse@testing php${V}-pecl@testing php${V}-redis@testing php${V}-memcached@testing

EXPOSE          9000
