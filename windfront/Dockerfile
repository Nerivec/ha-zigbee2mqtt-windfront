# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM

# Execute during the build of the image
ARG TEMPIO_VERSION BUILD_ARCH
RUN \
    curl -sSLf -o /usr/bin/tempio \
    "https://github.com/home-assistant/tempio/releases/download/${TEMPIO_VERSION}/tempio_${BUILD_ARCH}"

# Add nginx and create the run folder for nginx
RUN \
  apk --no-cache add nginx gettext-envsubst tzdata \
  && mkdir -p /run/nginx \
  && mkdir -p /usr/share/nginx/html

# Copy root filesystem
COPY rootfs /

ARG WINDFRONT_VERSION
RUN \
    curl -sSLf -O "https://github.com/Nerivec/zigbee2mqtt-windfront/releases/download/${WINDFRONT_VERSION}/zigbee2mqtt-windfront-${WINDFRONT_VERSION}.tar.gz" \
    && tar -C /usr/share/nginx/html/ --strip-components=1 -xf "zigbee2mqtt-windfront-${WINDFRONT_VERSION}.tar.gz" \
    && rm -rf "zigbee2mqtt-windfront-${WINDFRONT_VERSION}.tar.gz"
