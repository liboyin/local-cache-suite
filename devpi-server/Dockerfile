FROM python:3.12-slim
ENV DEBIAN_FRONTEND=noninteractive
COPY devpi-server.yaml supervisord.conf /
VOLUME /var/cache/devpi-server
RUN apt-get update && \
    apt-get install -y --no-install-recommends supervisor && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    pip --disable-pip-version-check --no-cache-dir install devpi-server && \
    devpi-init -c devpi-server.yaml && \
    devpi-gen-config
EXPOSE 3141
CMD ["supervisord", "-c", "supervisord.conf"]

