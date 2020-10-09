FROM nginx:stable-alpine

LABEL \
    maintainer="Morgan AUCHEDE <morgan.auchede@gmail.com>"

ENV \
    S6_BEHAVIOUR_IF_STAGE2_FAILS=2 \
    S6_KEEP_ENV=1 \
    S6_READ_ONLY_ROOT=1

RUN set -e -u -x \
\
    # Install packages
\
    && apk add --no-cache --no-progress --virtual BUILD_DEPS curl gnupg \
    && apk add --no-cache --no-progress bash ca-certificates shadow tzdata \
\
    # Install dockerize
\
    && curl --location "https://github.com/jwilder/dockerize/releases/download/v0.6.1/dockerize-linux-amd64-v0.6.1.tar.gz" | tar --directory /usr/local/bin --extract --gzip \
    && chmod +x /usr/local/bin/dockerize \
\
    # Install s6-overlay
\
    && curl "https://keybase.io/justcontainers/key.asc" | gpg --import \
    && curl --location --output /tmp/s6-overlay.tar.gz "https://github.com/just-containers/s6-overlay/releases/download/v2.1.0.0/s6-overlay-amd64.tar.gz" \
    && curl --location --output /tmp/s6-overlay.tar.gz.sig "https://github.com/just-containers/s6-overlay/releases/download/v2.1.0.0/s6-overlay-amd64.tar.gz.sig" \
    && gpg --verify /tmp/s6-overlay.tar.gz.sig /tmp/s6-overlay.tar.gz \
    && tar --directory / --extract --file /tmp/s6-overlay.tar.gz --gzip \
\
    # Clean
\
    && apk del --no-progress BUILD_DEPS \
    && rm -f -r /root/.gnupg /tmp/*

COPY rootfs/ /

ENTRYPOINT [ "/init" ]
