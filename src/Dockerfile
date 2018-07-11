FROM nginx:stable-alpine

LABEL \
    maintainer="Morgan Auchede <morgan.auchede@gmail.com>"

ENV \
    USER=nginx \
    S6_BEHAVIOUR_IF_STAGE2_FAILS=2 \
    S6_KEEP_ENV=1 \
    S6_READ_ONLY_ROOT=1

RUN set -ex \
\
    # Install packages
\
    && apk add --no-cache --no-progress --virtual BUILD_DEPS \
           curl \
    && apk add --no-cache --no-progress \
           bash \
\
    # Install timonier/dumb-entrypoint
\
    && curl --location "https://github.com/timonier/dumb-entrypoint/raw/master/src/s6-overlay/installer" | INSTALL_DIRECTORY="/usr/sbin" sh -s -- install \
\
    # Clean
\
    && apk del --no-progress \
           BUILD_DEPS \
    && rm -f -r \
           /etc/nginx/nginx.conf \
           /tmp/*

COPY ./rootfs /

ENTRYPOINT [ "/init" ]

VOLUME [ "/run" , "/var/cache" , "/tmp" ]
