# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM=ghcr.io/home-assistant/base:3.23
FROM ${BUILD_FROM}

ARG WINDFRONT_VERSION=v2.12.0

RUN \
    apk --no-cache add nginx gettext-envsubst tzdata \
    && mkdir -p /run/nginx \
    && mkdir -p /var/www/windfront \
    && curl -sSLf -O "https://github.com/Nerivec/zigbee2mqtt-windfront/releases/download/${WINDFRONT_VERSION}/zigbee2mqtt-windfront-${WINDFRONT_VERSION}.tar.gz" \
    && tar -C /var/www/windfront --strip-components=1 -zxvf "zigbee2mqtt-windfront-${WINDFRONT_VERSION}.tar.gz" \
    && rm -rf "zigbee2mqtt-windfront-${WINDFRONT_VERSION}.tar.gz" /tmp/* /etc/nginx \
    && chown -R root:root /var/www/windfront

# Copy root filesystem
COPY rootfs /

LABEL \
    org.opencontainers.image.title="Home Assistant Add-on: Zigbee2MQTT WindFront" \
    org.opencontainers.image.description="Zigbee2MQTT WindFront standalone frontend." \
    org.opencontainers.image.source="https://github.com/Nerivec/ha-zigbee2mqtt-windfront" \
    org.opencontainers.image.licenses="Apache License 2.0"
