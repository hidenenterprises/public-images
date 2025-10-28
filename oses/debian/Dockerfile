FROM        --platform=$TARGETOS/$TARGETARCH debian:buster-slim

LABEL author="Michael Parker" maintainer="parker@pterodactyl.io"
LABEL org.opencontainers.image.source="https://github.com/hidencloud/images"
LABEL org.opencontainers.image.licenses=MIT

# Switch to archived Debian repositories (since buster is EOL)
RUN echo "deb http://archive.debian.org/debian buster main contrib non-free" > /etc/apt/sources.list && \
    echo "deb http://archive.debian.org/debian-security buster/updates main contrib non-free" >> /etc/apt/sources.list && \
    echo "Acquire::Check-Valid-Until \"false\";" > /etc/apt/apt.conf.d/99no-check-valid && \
    apt -o Acquire::Check-Valid-Until=false update && \
    apt -o Acquire::Check-Valid-Until=false upgrade -y && \
    apt install -y --no-install-recommends \
        gcc g++ libgcc1 libc++-dev gdb libc6 git wget curl tar zip unzip binutils xz-utils \
        liblzo2-2 cabextract iproute2 net-tools netcat telnet libatomic1 \
        libsdl1.2debian libsdl2-2.0-0 libfontconfig libicu63 icu-devtools libunwind8 \
        libssl-dev sqlite3 libsqlite3-dev libmariadbclient-dev libduktape203 locales ffmpeg \
        gnupg2 apt-transport-https software-properties-common ca-certificates tzdata \
        liblua5.3 libz-dev rapidjson-dev && \
    update-locale lang=en_US.UTF-8 && \
    dpkg-reconfigure --frontend noninteractive locales && \
    useradd -m -d /home/container -s /bin/bash container && \
    apt clean && rm -rf /var/lib/apt/lists/*

USER        container
ENV         USER=container \
            HOME=/home/container \
            DEBIAN_FRONTEND=noninteractive

WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
