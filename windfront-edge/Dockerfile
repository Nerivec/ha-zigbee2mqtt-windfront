# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM

ARG WINDFRONT_VERSION

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

COPY rootfs /
