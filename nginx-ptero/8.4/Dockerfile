# Same recipe as ghcr.io/sigma-production/nginx-ptero:8.4 (Alpine 3.22 with the edge repositories added),
# rebuilt because upstream hasn't published an image since 18-09-2025 and its PHP 8.4.12 is vulnerable to
# CVE-2026-109618 and CVE-2026-109619. php84 comes from edge, which has the fixed 8.4.27.
FROM alpine:3.22

LABEL author="Sigma-Production" maintainer="HIDENCLOUD" \
      org.opencontainers.image.source="https://github.com/hidenenterprises/public-images"

RUN echo "https://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories \
    && echo "https://dl-cdn.alpinelinux.org/alpine/edge/main" >> /etc/apk/repositories
RUN apk --update --no-cache add curl ca-certificates nginx
RUN apk add --no-cache php84 php84-xml php84-xmlwriter php84-exif php84-fpm php84-session php84-soap php84-openssl php84-gmp php84-pdo_odbc \
    php84-json php84-dom php84-pdo php84-zip php84-mysqli php84-sqlite3 php84-pdo_pgsql php84-bcmath php84-gd \
    php84-odbc php84-pdo_mysql php84-pdo_sqlite php84-gettext php84-xmlreader php84-bz2 php84-iconv php84-pdo_dblib \
    php84-curl php84-ctype php84-phar php84-fileinfo php84-mbstring php84-tokenizer php84-simplexml
# The egg's start scripts call php-fpm8
RUN mv /usr/sbin/php-fpm84 /usr/sbin/php-fpm8
# Fail the build if apk didn't bring a fixed PHP
RUN php84 -r 'exit(version_compare(PHP_VERSION, "8.4.27", "<") ? 1 : 0);'
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

USER container
ENV USER=container
ENV HOME=/home/container

WORKDIR /home/container
COPY ./entrypoint.sh /entrypoint.sh

CMD ["/bin/ash", "/entrypoint.sh"]
