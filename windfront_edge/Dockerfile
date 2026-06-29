# https://developers.home-assistant.io/docs/apps/configuration#app-dockerfile
ARG BUILD_FROM=ghcr.io/home-assistant/base:3.23
FROM ${BUILD_FROM}

# ignore cache for below layers when latest commit changes
ADD "https://api.github.com/repos/Nerivec/zigbee2mqtt-windfront/branches/built-main" latest_commit
RUN \
    apk --no-cache add nginx gettext-envsubst tzdata \
    && mkdir -p /run/nginx \
    && mkdir -p /var/www/windfront \
    && curl -sSLf -O "https://github.com/Nerivec/zigbee2mqtt-windfront/archive/refs/heads/built-main.tar.gz" \
    && tar -C /var/www/windfront --strip-components=1 -zxvf "built-main.tar.gz" \
    && rm -rf "built-main.tar.gz" /tmp/* /etc/nginx \
    && chown -R root:root /var/www/windfront

# Copy root filesystem
COPY rootfs /

LABEL \
    org.opencontainers.image.title="Home Assistant App: Zigbee2MQTT WindFront Edge" \
    org.opencontainers.image.description="Development version." \
    org.opencontainers.image.source="https://github.com/Nerivec/ha-zigbee2mqtt-windfront" \
    org.opencontainers.image.licenses="Apache License 2.0"
