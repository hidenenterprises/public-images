FROM node:21-bullseye-slim

LABEL author="Softwarenoob" maintainer="admin@softwarenoob.com"
LABEL org.opencontainers.image.source="https://github.com/hidencloud/images"
LABEL org.opencontainers.image.licenses="MIT"

# Use DEBIAN_FRONTEND to avoid interactive prompts
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get -y install --no-install-recommends \
        curl ffmpeg iproute2 git sqlite3 python3 tzdata \
        ca-certificates dnsutils build-essential locales \
    # ensure npm stays in the compatible 10.x line
    && npm install -g npm@10.9.2 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && useradd -m -d /home/container container \
    && locale-gen en_US.UTF-8

ENV LC_ALL=en_US.UTF-8 \
    LANG=en_US.UTF-8 \
    LANGUAGE=en_US.UTF-8 \
    USER=container \
    HOME=/home/container

USER container
WORKDIR /home/container

COPY ./entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]
