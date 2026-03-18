# Copyright 2026 The MathWorks, Inc.
ARG PLATFORM=amd64

FROM  --platform=linux/${PLATFORM} ubuntu:22.04

ARG PLATFORM

LABEL maintainer="The MathWorks"

COPY base-dependencies-${PLATFORM}.txt /tmp/base-dependencies.txt

RUN export DEBIAN_FRONTEND=noninteractive \
    && apt-get update \
    && apt-get install --no-install-recommends -y `cat /tmp/base-dependencies.txt` \
    && apt-get clean \
    && apt-get -y autoremove \
    && rm -rf /var/lib/apt/lists/*

RUN [ -d /usr/share/X11/xkb ] || mkdir -p /usr/share/X11/xkb

# To make sure non-ASCII data processed in UTF-8
ENV LANG=en_US.UTF-8

WORKDIR /
