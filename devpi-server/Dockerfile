FROM python:3.12-slim
ENV DEBIAN_FRONTEND=noninteractive
COPY devpi-server.yaml /
VOLUME /var/cache/devpi-server
RUN pip --disable-pip-version-check --no-cache-dir install devpi-server && \
    devpi-init -c devpi-server.yaml
EXPOSE 3141
CMD ["devpi-server", "-c", "devpi-server.yaml"]

