FROM            hwdm/aprunit
MAINTAINER      Howard Mei      <howardleomei@gmail.com>

ENV             V=1.10.3-r0
ENV             _SERVER_MODE="simple"
ENV             _SERVER_NAME="localhost"
ENV             _DOC_RPATH="html"
ENV             _SSL_CERT=""
ENV             _LISTEN_TO1="127.0.0.1:9000 max_fails=3 fail_timeout=3s"
ENV             _LISTEN_TO2="127.0.0.1:9001"
ENV             _LISTEN_TO3="127.0.0.1:9002"
# Support
ENV             _LB_METHOD="byrequest"

# Warning: ADD directive does not overwrite existing files. One of the duplicate file will be renamed to *.apk-new
COPY            etc             /etc
COPY            var             /var
COPY            usr             /usr


# Install nginx, its extensions and redirect example.com to www.example.com using ngsrename "${_SSL_CERT}" ${_SERVER_NAME} "www.${_SERVER_NAME}"
RUN             set -x && apk-install ca-certificates libressl pcre zlib nginx=${V} nginx-mod-http-fancyindex=${V} nginx-mod-http-upload-progress=${V} && \
                          chown -R www-data:www-data /var/www && \
                set +x && apk-cleanup


EXPOSE          80 443

