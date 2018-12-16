FROM nginx:stable-alpine

LABEL \
    maintainer="Morgan Auchede <morgan.auchede@gmail.com>"

ENV \
    S6_BEHAVIOUR_IF_STAGE2_FAILS=2 \
    S6_KEEP_ENV=1 \
    S6_READ_ONLY_ROOT=1

RUN set -e -u -x \
\
    # Install packages
\
    && apk add --no-cache --no-progress --virtual BUILD_DEPS curl \
    && apk add --no-cache --no-progress shadow \
\
    # Install dockerize
\
    && export $(curl --location "https://github.com/timonier/version-lister/raw/generated/jwilder/dockerize/latest" | xargs) \
    && curl --location "${DOCKERIZE_RELEASE}" | tar --directory /tmp --extract --gzip \
    && mv /tmp/dockerize /usr/bin/dockerize \
\
    # Install s6-overlay
\
    && curl --location "https://github.com/timonier/dumb-entrypoint/raw/master/src/s6-overlay/installer" | sh -s -- install \
\
    # Clean
\
    && apk del --no-progress BUILD_DEPS \
    && rm -f -r /tmp/*

COPY rootfs/. /

ENTRYPOINT [ "/init" ]
