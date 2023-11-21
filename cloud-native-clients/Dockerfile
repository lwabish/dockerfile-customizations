FROM docker:24.0.7-cli-alpine3.18

WORKDIR /data

RUN apk add --update --no-cache ca-certificates curl bash openssh-client busybox-extras

# kubectl
ARG KUBE_VERSION="v1.24.10"
RUN curl -L https://storage.googleapis.com/kubernetes-release/release/${KUBE_VERSION}/bin/linux/amd64/kubectl -o /usr/local/bin/kubectl \
    && chmod +x /usr/local/bin/kubectl

# helm
ARG HELM_VERSION="v3.12.3"
RUN curl -L https://get.helm.sh/helm-${HELM_VERSION}-linux-amd64.tar.gz -o helm-${HELM_VERSION}-linux-amd64.tar.gz \
    && tar -xvf helm-${HELM_VERSION}-linux-amd64.tar.gz \
    && mv linux-amd64/helm /usr/local/bin \
    && rm -f ./helm-${HELM_VERSION}-linux-amd64.tar.gz \
    && rm -rf ./linux-amd64

# virtctl
ARG VIRTCTL_VERSION=v1.1.0
RUN curl -L -o /usr/local/bin/virtctl \
    "https://github.com/kubevirt/kubevirt/releases/download/${VIRTCTL_VERSION}/virtctl-${VIRTCTL_VERSION}-linux-amd64" \
    && chmod +x /usr/local/bin/virtctl

RUN mkdir -p /root/.ssh \
    && echo "StrictHostKeyChecking no" >> /root/.ssh/config \
    && echo "UserKnownHostsFile /dev/null" >> /root/.ssh/config \
    && chmod 600 /root/.ssh/config \
    && chmod 700 /root/.ssh \
    && ssh-keygen -t rsa -f /root/.ssh/id_rsa -q -P ""

ENTRYPOINT [ "/bin/bash" ]

