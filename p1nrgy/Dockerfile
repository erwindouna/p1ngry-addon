ARG BUILD_FROM=busybox:dummy
FROM $BUILD_FROM
ARG BUILD_ARCH
ARG HA_RELEASE

ENV LANG=C.UTF-8
# Copy data for add-on
COPY config.yaml /app/ha_addon_version.json
COPY rootfs /

# Labels
LABEL \
  io.hass.version=$HA_RELEASE \
  io.hass.type="addon" \
  io.hass.arch=$BUILD_ARCH \
  org.opencontainers.image.title="Home Assistant Add-on: p1nrgy"  \
  org.opencontainers.image.description="p1nrgy is a Home Assistant add-on to passthrough P1 data to MQTT"  \
  org.opencontainers.image.source="https://github.com/erwindouna/p1nrgy-addon" \
  org.opencontainers.image.licenses="Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)"