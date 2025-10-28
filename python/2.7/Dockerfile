FROM python:2.7-slim

LABEL author="Software-noob" maintainer="admin@softwarenoob.com"
LABEL org.opencontainers.image.source="https://github.com/hidencloud/images"
LABEL org.opencontainers.image.licenses="MIT"

# --- switch to archived Debian repos so buster works again ---
RUN echo "deb http://archive.debian.org/debian buster main contrib non-free" > /etc/apt/sources.list && \
    echo "deb http://archive.debian.org/debian-security buster/updates main contrib non-free" >> /etc/apt/sources.list && \
    echo "Acquire::Check-Valid-Until \"false\";" > /etc/apt/apt.conf.d/99no-check-valid && \
    apt-get -o Acquire::Check-Valid-Until=false update && \
    apt-get -y install --no-install-recommends \
        git gcc g++ ca-certificates dnsutils curl iproute2 ffmpeg procps locales && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    locale-gen en_US.UTF-8

ENV LC_ALL=en_US.UTF-8 \
    LANG=en_US.UTF-8 \
    LANGUAGE=en_US.UTF-8 \
    DEBIAN_FRONTEND=noninteractive \
    USER=container \
    HOME=/home/container

# --- create the container user safely ---
RUN useradd -m -d /home/container -s /bin/bash container

USER container
WORKDIR /home/container

COPY ./entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]
