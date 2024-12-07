# https://github.com/sameersbn/docker-apt-cacher-ng/blob/master/Dockerfile
FROM debian:bookworm-slim

ENV APT_CACHER_NG_VERSION=3.7.4 \
    APT_CACHER_NG_CACHE_DIR=/var/cache/apt-cacher-ng \
    APT_CACHER_NG_LOG_DIR=/var/log/apt-cacher-ng \
    APT_CACHER_NG_USER=apt-cacher-ng \
    DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install --no-install-recommends -y apt-cacher-ng=${APT_CACHER_NG_VERSION}* ca-certificates wget && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    sed 's/# ForeGround: 0/ForeGround: 1/' -i /etc/apt-cacher-ng/acng.conf && \
    sed 's/# PassThroughPattern:.*this would allow.*/PassThroughPattern: .* #/' -i /etc/apt-cacher-ng/acng.conf && \
    wget https://raw.githubusercontent.com/sameersbn/docker-apt-cacher-ng/refs/heads/master/entrypoint.sh -O /sbin/entrypoint.sh && \
    chmod 755 /sbin/entrypoint.sh

EXPOSE 3142/tcp

ENTRYPOINT ["/sbin/entrypoint.sh"]

CMD ["/usr/sbin/apt-cacher-ng"]
