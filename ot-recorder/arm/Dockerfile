#
# Dockerfile for ot-recorder-arm
#

FROM armhf/debian:jessie
MAINTAINER EasyPi Software Foundation

RUN set -xe \
    && apt-get update \
    && apt-get install -y curl \
    && curl -sSL http://repo.owntracks.org/repo.owntracks.org.gpg.key | apt-key add - \
    && echo 'deb http://repo.owntracks.org/debian jessie main' > /etc/apt/sources.list.d/owntracks.list \
    && apt-get update \
    && apt-get install -y ot-recorder \
    && rm -rf /var/lib/apt/lists/*

ENV OTR_STORAGEDIR /var/spool/owntracks/recorder/store
ENV OTR_HOST       iot.eclipse.org
ENV OTR_PORT       1883
ENV OTR_TOPICS     owntracks/#

VOLUME $OTR_STORAGEDIR

COPY docker-entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]

EXPOSE 8083
