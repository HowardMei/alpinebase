FROM            hwdm/aprunit
MAINTAINER      Howard Mei      <howardleomei@gmail.com>

ENV				V=1.10.3-r0

# Warning: ADD directive does not overwrite existing files. One of the duplicate file will be renamed to *.apk-new
COPY 			etc 			/etc
COPY 			var 			/var


# Install php, its extensions and composer
RUN 			set -x && apk-install ca-certificates libressl pcre zlib nginx=${V} nginx-mod-http-fancyindex=${V} nginx-mod-http-upload-progress=${V} && \
						  chown -R www-data:www-data /var/www && \
				set +x && apk-cleanup


EXPOSE 			80 443

