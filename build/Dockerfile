FROM centos:latest
LABEL maintainer="wlfkongl@163.com"
ENV NPS_SERVER_BIN_URL  https://github.com/ehang-io/nps/releases/download/v0.26.7/linux_amd64_server.tar.gz
RUN yum install -y wget;
RUN mkdir -p /nps;cd /nps ; wget -c  ${NPS_SERVER_BIN_URL} ; tar xvzf linux_amd64_server.tar.gz; ./nps install; cd /; rm -rf /nps;
RUN yum clean all && rm -rf /var/cache/yum;
EXPOSE 80 443 8080
# VOLUME [ "/etc/nps/conf/nps.conf" ]
CMD ["nps" , "start"]
