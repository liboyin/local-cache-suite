FROM python:3.13-slim
ENV DEBIAN_FRONTEND=noninteractive
COPY devpi-server.yaml /
RUN pip --disable-pip-version-check --no-cache-dir install devpi-server && \
    devpi-init -c devpi-server.yaml
EXPOSE 3141
CMD ["devpi-server", "-c", "devpi-server.yaml"]
