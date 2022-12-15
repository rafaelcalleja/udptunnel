IMG_REPO ?= rafaelcalleja
IMG_TAG ?= $(OPENWRT_VERSION)-udptunnel
IMG_NAME ?= openwrt-sdk

UDPTUNNEL_REPOSITORY ?= https://github.com/rafaelcalleja/udptunnel
UDPTUNNEL_VERSION ?= master

OPENWRT_VERSION ?= ramips-mt7621-18.06.7

.PHONY: default
default: build

.PHONY: build
build:
	docker build -t $(IMG_REPO)/$(IMG_NAME):$(IMG_TAG) -f Dockerfile \
    	--build-arg UDPTUNNEL_REPOSITORY=$(UDPTUNNEL_REPOSITORY) \
    	--build-arg UDPTUNNEL_VERSION=$(UDPTUNNEL_VERSION) \
    	--build-arg OPENWRT_VERSION=$(OPENWRT_VERSION) \
    	.

push:
	docker push $(IMG_REPO)/$(IMG_NAME):$(IMG_TAG)
