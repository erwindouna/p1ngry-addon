ARG BUILD_FROM="ghcr.io/hassio-addons/base:19.0.0"
FROM ${BUILD_FROM}

ARG BUILD_ARCH
ARG BUILD_VERSION="dev"
ARG P1NRGY_VERSION="0.0.4"

ENV S6_VERBOSITY="1"

RUN apk add --no-cache curl jq tar

RUN set -eux; \
    mkdir -p /app; \
    printf '{"version":"%s"}\n' "${BUILD_VERSION}" > /app/ha_addon_version.json

COPY rootfs/ /

RUN set -eux; \
    case "${BUILD_ARCH}" in \
        aarch64) release_arch="arm64" ;; \
        amd64)  release_arch="amd64" ;; \
        *) echo "Unsupported architecture: ${BUILD_ARCH}" >&2; exit 1 ;; \
    esac; \
    release_tag="v${P1NRGY_VERSION}"; \
    artifact="p1nrgy_${P1NRGY_VERSION}_linux_${release_arch}.tar.gz"; \
    url="https://github.com/erwindouna/p1ngry/releases/download/${release_tag}/${artifact}"; \
    curl -fL "${url}" -o /tmp/p1nrgy.tar.gz; \
    tar -xzf /tmp/p1nrgy.tar.gz -C /usr/bin p1nrgy; \
    chmod +x /usr/bin/p1nrgy; \
    rm -f /tmp/p1nrgy.tar.gz

ARG BUILD_DATE
ARG BUILD_DESCRIPTION
ARG BUILD_NAME
ARG BUILD_REF
ARG BUILD_REPOSITORY

LABEL \
    io.hass.name="${BUILD_NAME}" \
    io.hass.description="${BUILD_DESCRIPTION}" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version="${BUILD_VERSION}" \
    maintainer="Erwin Douna <e.douna@gmail.com>" \
    org.opencontainers.image.title="${BUILD_NAME}" \
    org.opencontainers.image.description="${BUILD_DESCRIPTION}" \
    org.opencontainers.image.vendor="Erwin Douna <e.douna@gmail.com>" \
    org.opencontainers.image.authors="Erwin Douna <e.douna@gmail.com>" \
    org.opencontainers.image.licenses="MIT" \
    org.opencontainers.image.url="https://github.com/${BUILD_REPOSITORY}" \
    org.opencontainers.image.source="https://github.com/${BUILD_REPOSITORY}" \
    org.opencontainers.image.documentation="https://github.com/${BUILD_REPOSITORY}/blob/main/README.md" \
    org.opencontainers.image.created="${BUILD_DATE}" \
    org.opencontainers.image.revision="${BUILD_REF}" \
    org.opencontainers.image.version="${BUILD_VERSION}"