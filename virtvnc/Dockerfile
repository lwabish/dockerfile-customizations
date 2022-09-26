FROM alpine:3.16.2 as fetcher

ARG NOVNC="v1.3.0"

WORKDIR /source

RUN apk --no-cache add curl unzip && \
    curl -L -o /source/novnc.zip https://github.com/novnc/noVNC/archive/refs/tags/${NOVNC}.zip && \
    unzip /source/novnc.zip && \
    mv /source/noVNC-* /source/novnc

FROM bitnami/kubectl:1.21.14 as app

WORKDIR /static

COPY --from=fetcher /source/novnc/app /static/app
COPY --from=fetcher /source/novnc/core /static/core
COPY --from=fetcher /source/novnc/vendor /static/vendor
COPY --from=fetcher /source/novnc/*.html /static/

CMD ["proxy", "--www=/static", "--accept-hosts=^.*$", "--address=[::]", "--api-prefix=", "--www-prefix="]
