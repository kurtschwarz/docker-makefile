#vim: set ft=dockerfile:

FROM example/alpine:3.6

ARG PYTHON_VERSION

RUN set -euxo pipefail && \
    apk add --no-cache --update \
        python=$PYTHON_VERSION && \
    rm -rf /tmp/* \
        /usr/include \
        /var/cache/apk/* \
        /usr/share/man
