#vim: set ft=dockerfile:

FROM alpine:3.6

ARG CURL_VERSION

RUN set -euxo pipefail && \
    apk add --no-cache --update \
        curl=$CURL_VERSION && \
    rm -rf /tmp/* \
        /usr/include \
        /var/cache/apk/* \
        /usr/share/man
