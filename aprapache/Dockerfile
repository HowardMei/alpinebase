FROM            hwdm/aprunit
MAINTAINER      Howard Mei      <howardleomei@gmail.com>

ENV             V=2.4.25-r0
# _SERVER_MODE options: default/direct, fcgiport/FCGIPORT, fcgisock/FCGISOCK, fcgilb2/FCGILB2, fcgilb3/FCGILB3
ENV             _SERVER_MODE="default"
ENV             _DOMAIN="localhost"
ENV             _SERVER_ALIAS="localhost"
ENV             _DOC_ROOT="/var/www/localhost/htdocs"
ENV             _SSL_CERT=""
ENV             _LISTEN_TO1="127.0.0.1:9000"
ENV             _LISTEN_TO2="127.0.0.1:9001"
ENV             _LISTEN_TO3="127.0.0.1:9002"
# Support
ENV             _LB_METHOD="byrequest"

# Add the files
ADD             etc             /etc

# Install apache2 and its extensions. apache2-proxy contains php fastcgi module. apache2-mod-wsgi contains python wsgi module.
RUN             set -x && apk-install ca-certificates apache2=${V} apache2-lua=${V} apache2-proxy=${V} apache2-proxy-html=${V} apache2-ssl=${V} && \
                            ln -sf /usr/lib/libxml2.so.2 /usr/lib/libxml2.so && \
                            mkdir -p /var/run/apache2 /var/log/apache2 /var/www/html && ln -sf /var/run/apache2 /run && \
                            chown -R www-data:www-data /var/www/html /run/apache2 /var/run/apache2 /var/log/apache2 && \
                set +x && apk-cleanup

EXPOSE          80 443
