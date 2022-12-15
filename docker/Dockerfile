ARG OPENWRT_VERSION
FROM openwrtorg/sdk:${OPENWRT_VERSION}

ARG UDPTUNNEL_VERSION=master
ENV UDPTUNNEL_VERSION ${UDPTUNNEL_VERSION}

ARG UDPTUNNEL_REPOSITORY=https://github.com/rafaelcalleja/udptunnel
ENV UDPTUNNEL_REPOSITORY ${UDPTUNNEL_REPOSITORY}

ENV STAGING_DIR /home/build/openwrt/staging_dir
ENV TOOLCHAIN_DIR ${STAGING_DIR}/toolchain-mipsel_24kc_gcc-7.3.0_musl

WORKDIR /app

USER root
RUN apt update -yq && apt install -y pkg-config && \
    rm -rf /var/lib/apt/lists/*

RUN git clone ${UDPTUNNEL_REPOSITORY} udptunnel && \
    cd udptunnel && \
    git branch -a && \
    git tag && \
    git checkout ${UDPTUNNEL_VERSION} && \
    make CC=${TOOLCHAIN_DIR}/bin/mipsel-openwrt-linux-gcc-7.3.0 LD=${TOOLCHAIN_DIR}/bin/mipsel-openwrt-linux-ld

