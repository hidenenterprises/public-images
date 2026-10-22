# Same recipe as ghcr.io/sigma-production/nginx-ptero:8.3 (Alpine 3.22 with the edge repositories added),
# rebuilt because upstream hasn't published an image since 18-09-2025 and its PHP 8.3 build is vulnerable to
# CVE-2026-109618 and CVE-2026-109619. php83 comes from edge, which has the fixed 8.3.36.
FROM alpine:3.22

LABEL author="Sigma-Production" maintainer="HIDENCLOUD" \
      org.opencontainers.image.source="https://github.com/hidenenterprises/public-images"

RUN echo "https://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories \
    && echo "https://dl-cdn.alpinelinux.org/alpine/edge/main" >> /etc/apk/repositories
RUN apk --update --no-cache add curl ca-certificates nginx
RUN apk add --no-cache php83 php83-xml php83-xmlwriter php83-exif php83-fpm php83-session php83-soap php83-openssl php83-gmp php83-pdo_odbc \
    php83-json php83-dom php83-pdo php83-zip php83-mysqli php83-sqlite3 php83-pdo_pgsql php83-bcmath php83-gd \
    php83-odbc php83-pdo_mysql php83-pdo_sqlite php83-gettext php83-xmlreader php83-bz2 php83-iconv php83-pdo_dblib \
    php83-curl php83-ctype php83-phar php83-fileinfo php83-mbstring php83-tokenizer php83-simplexml
# The egg's start scripts call php-fpm8
RUN mv /usr/sbin/php-fpm83 /usr/sbin/php-fpm8
# Fail the build if apk didn't bring a fixed PHP
RUN php83 -r 'exit(version_compare(PHP_VERSION, "8.3.36", "<") ? 1 : 0);'
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

USER container
ENV USER=container
ENV HOME=/home/container

WORKDIR /home/container
COPY ./entrypoint.sh /entrypoint.sh

CMD ["/bin/ash", "/entrypoint.sh"]
