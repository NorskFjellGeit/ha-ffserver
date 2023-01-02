ARG BUILD_FROM
FROM $BUILD_FROM

FROM alpine:3.8
FROM ${BUILD_FROM}

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

RUN apk add curl bash ffmpeg && \
    rm -rf /var/cache/apk/*
COPY run.sh /usr/bin/run.sh
RUN chmod +x /usr/bin/run.sh
COPY ffserver.conf /etc/ffserver.conf
ENV RTSP_URL rtsp://freja.hiof.no:1935/rtplive/definst/hessdalen03.stream
ENV FFMPEG_INPUT_OPTS  ""
ENV FFMPEG_OUTPUT_OPTS  ""
ENV FFSERVER_LOG_LEVEL "error"
ENV FFMPEG_LOG_LEVEL  "warning"
ENTRYPOINT run.sh
