FROM alpine:3.16.2 as fetcher

ARG NOVNC="v1.4.0"

WORKDIR /source

RUN apk --no-cache add curl unzip && \
    curl -L -o /source/novnc.zip https://github.com/novnc/noVNC/archive/refs/tags/${NOVNC}.zip && \
    unzip /source/novnc.zip && \
    mv /source/noVNC-* /source/novnc

FROM bitnami/kubectl:1.21.14 as app

WORKDIR /static

COPY --from=fetcher /source/novnc /static

# api-prefix需要是www-prefix的子集
# 如果不通，看console日志看websocket拼接的地址是什么，是否可达
CMD ["proxy", "--www=/static", "--accept-hosts=^.*$", "--address=[::]", "--api-prefix=/vnc/k8s", "--www-prefix=/vnc/"]
