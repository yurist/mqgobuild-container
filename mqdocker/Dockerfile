FROM centos:latest

USER 0

ARG MQ_ARCHIVE="mqadv_dev921_linux_x86-64.tar.gz"

COPY $MQ_ARCHIVE /tmp

RUN cd /tmp && \
    tar -C . -zxvf $MQ_ARCHIVE && \
    cd MQServer && \
    ./mqlicense.sh -accept && \
    rpm -ivh MQSeriesRuntime*.rpm MQSeriesSDK*.rpm && \
    cd /tmp && \
    rm $MQ_ARCHIVE && \
    rm -rf MQServer
