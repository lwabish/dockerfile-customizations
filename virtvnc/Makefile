registry=dockerhub.kubekey.local:7443/kubevirt/

default: build push

build:
	docker build -t $(registry)/virtvnc:1.21.14-1.3.0

push:
	docker push $(registry)/virtvnc:1.21.14-1.3.0
