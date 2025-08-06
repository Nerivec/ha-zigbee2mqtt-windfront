# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM AS base

RUN \
    apk --no-cache add nginx gettext-envsubst tzdata \
    && mkdir -p /run/nginx \
    && mkdir -p /var/www/windfront \
    && rm -rf /tmp/* /etc/nginx

ARG WINDFRONT_VERSION

FROM base AS build

# ignore cache for below layers when latest commit changes
ADD "https://api.github.com/repos/Nerivec/zigbee2mqtt-windfront/branches/main" latest_commit
RUN \
    apk --no-cache add nodejs npm git \
    && git clone -b main --single-branch --depth 1 https://github.com/Nerivec/zigbee2mqtt-windfront.git /app \
    && cd /app \
    && npm ci \
    && NODE_ENV=production npm run build

FROM base AS release

COPY rootfs /
COPY --from=build /app/dist /var/www/windfront

RUN chown -R root:root /var/www/windfront
