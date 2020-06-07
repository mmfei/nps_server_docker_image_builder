FROM centos:latest
LABEL maintainer="wlfkongl@163.com"
ENV NPS_SERVER_BIN_URL https://github.com/ehang-io/nps/releases/download/v0.26.7/linux_amd64_client.tar.gz 
RUN yum install -y wget;
RUN mkdir -p /npc;cd /npc ; wget -c  ${NPS_SERVER_BIN_URL} ; tar xvzf linux_amd64_client.tar.gz; 
WORKDIR /npc
RUN yum clean all && rm -rf /var/cache/yum;
# VOLUME [ "/npc/conf/npc.conf" ]
CMD ["/npc/npc"]
