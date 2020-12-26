ARG BUILD_FROM=hassioaddons/base:latest
# hadolint ignore=DL3006
FROM ${BUILD_FROM}
ARG NETDATA_VERSION="v1.23.2"

# Set shell
SHELL ["/bin/bash", "-x" ,"-o", "pipefail", "-c"]

# Setup base
RUN \
    apk add --no-cache alpine-sdk bash curl libuv-dev zlib-dev util-linux-dev libmnl-dev gcc make git autoconf automake pkgconfig python3 logrotate cmake libressl-dev && \
    apk add --no-cache -U nodejs && \
    cd /usr/local/share/ && git clone --depth 1 --branch ${NETDATA_VERSION} https://github.com/netdata/netdata.git && \
    cd netdata && \
    ./netdata-installer.sh 
    
# Copy root filesystem
COPY rootfs /

# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="Netdata" \
    io.hass.description="Monitor everything in real time – for free." \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Regis A. Despres <kalw@addons.community>" \
    org.opencontainers.image.title="Netdata" \
    org.opencontainers.image.description="Monitor everything in real time – for free." \
    org.opencontainers.image.vendor="Home Assistant Community Add-ons" \
    org.opencontainers.image.authors="Regis A. Despres <kalw@indolore.net>" \
    org.opencontainers.image.licenses="MIT" \
    org.opencontainers.image.url="https://github.com/kalw/hassio-addons/blob/master/netdata/" \
    org.opencontainers.image.source="https://github.com/kalw/hassio-addons/blob/master/netdata/" \
    org.opencontainers.image.documentation="https://github.com/kalw/hassio-addons/blob/master/netdata/README" \
    org.opencontainers.image.created=${BUILD_DATE} \
    org.opencontainers.image.revision=${BUILD_REF} \
    org.opencontainers.image.version=${BUILD_VERSION}
