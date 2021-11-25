FROM docker

# kubectl
ARG KUBE_VERSION="v1.18.10"
RUN apk add --update ca-certificates \
    && apk add --update -t deps curl \
    && apk add --update gettext \
    && apk add --update git \
    && curl -L https://storage.googleapis.com/kubernetes-release/release/${KUBE_VERSION}/bin/linux/amd64/kubectl -o /usr/local/bin/kubectl \
    && chmod +x /usr/local/bin/kubectl \
    && apk del --purge deps \
    && rm /var/cache/apk/*

# helm
ARG HELM_VERSION="v3.2.1"
RUN apk add --update ca-certificates \
    && apk add --update -t deps wget git openssl bash \
    && wget https://get.helm.sh/helm-${HELM_VERSION}-linux-amd64.tar.gz \
    && tar -xvf helm-${HELM_VERSION}-linux-amd64.tar.gz \
    && mv linux-amd64/helm /usr/local/bin \
    && apk del --purge deps \
    && rm /var/cache/apk/* \
    && rm -f /helm-${HELM_VERSION}-linux-amd64.tar.gz

ENTRYPOINT [ "/bin/sh" ]