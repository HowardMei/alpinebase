FROM            hwdm/aps6base
MAINTAINER      Howard Mei      <howardleomei@gmail.com>

ENV				V=1.10.3

# Add the files
ADD 			etc 			/etc
ADD 			var 			/var


# Install php, its extensions and composer
RUN 			set -x && apk-install ca-certificates libressl pcre zlib geoip libgd@edge libwebp@edge \
							nginx nginx-mod-http-fancyindex nginx-mod-http-upload-progress \
							nginx-mod-http-image-filter nginx-mod-http-geoip && \
						  chown -R www-data:www-data /var/www /var/lib/nginx /var/run/nginx /var/log/nginx && \
				set +x && apk-cleanup

# Activate s6-fdholderd by default, or else stage2 might fail during cont-init
RUN 			s6-rmrf /etc/s6/services/s6-fdholderd/down

EXPOSE 			80 443
