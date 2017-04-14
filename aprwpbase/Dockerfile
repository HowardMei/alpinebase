FROM            hwdm/aprphpfpm
MAINTAINER      Howard Mei      <howardleomei@gmail.com>

ENV				WV=7

# Add the files
ADD 			etc 			/etc
ADD 			var 			/var

# Install git, wordpress
RUN 			set -x && apk-install git && \

				set +x && apk-cleanup

EXPOSE 			9000
