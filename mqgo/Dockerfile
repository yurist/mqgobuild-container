FROM mq-docker

USER 0

ARG GO_ARCHIVE="go1.14.13.linux-amd64.tar.gz"

COPY $GO_ARCHIVE /tmp

RUN tar -C /usr/local -xzf /tmp/$GO_ARCHIVE && \
    rm /tmp/$GO_ARCHIVE && \
    yum -y install git && \
    yum -y group install "Development Tools"

