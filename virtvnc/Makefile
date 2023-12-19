registry=dockerhub.kubekey.local:7443/kubevirt
tag=1.1.0

default: build push

build:
	docker build -t $(registry)/virtvnc:$(tag) .

push:
	docker push $(registry)/virtvnc:$(tag)
