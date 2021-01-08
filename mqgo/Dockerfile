FROM mq-docker

USER 0

COPY go1.14.13.linux-amd64.tar.gz /tmp

RUN tar -C /usr/local -xzf /tmp/go1.14.13.linux-amd64.tar.gz && \
    export PATH=$PATH:/usr/local/go/bin && \
    yum -y install git && \
    yum -y group install "Development Tools"

