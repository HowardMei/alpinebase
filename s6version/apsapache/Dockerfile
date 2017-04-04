FROM            hwdm/aps6mark
MAINTAINER      Howard Mei      <howardleomei@gmail.com>

ENV				V=2.4.25-r0

# Add the files
ADD 			etc 			/etc
ADD 			var 			/var


# Install php, its extensions and composer
RUN 			set -x && apk-install ca-certificates apache2=${V} && \
							chown -R www-data:www-data /var/www /var/run/apache2 /var/log/apache2 && \
				set +x && apk-cleanup

# Activate s6-fdholderd by default, or else stage2 might fail during cont-init
RUN 			s6-rmrf /etc/s6/services/s6-fdholderd/down

EXPOSE 			80 443
