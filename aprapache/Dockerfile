FROM            hwdm/aprunit
MAINTAINER      Howard Mei      <howardleomei@gmail.com>

ENV				V=2.4.25-r0

# Add the files
ADD 			etc 			/etc

# Install apache2 and its extensions. apache2-proxy contains php fastcgi module. apache2-mod-wsgi contains python wsgi module.
RUN 			set -x && apk-install ca-certificates apache2=${V} apache2-lua=${V} apache2-proxy=${V} apache2-proxy-html=${V} apache2-ssl=${V} && \
							ln -sf /usr/lib/libxml2.so.2 /usr/lib/libxml2.so && \
							mkdir -p /var/run/apache2 /var/log/apache2 /var/www/html && ln -sf /var/run/apache2 /run && \
							chown -R www-data:www-data /var/www/html /run/apache2 /var/run/apache2 /var/log/apache2 && \
				set +x && apk-cleanup

EXPOSE 			80 443
