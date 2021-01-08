FROM centos:latest

USER 0

COPY mqadv_dev921_linux_x86-64.tar.gz /tmp

RUN cd /tmp && \
    tar -C . -zxvf mqadv_dev921_linux_x86-64.tar.gz && \
    cd MQServer && \
    ./mqlicense.sh -accept && \
    rpm -ivh MQSeries*.rpm
