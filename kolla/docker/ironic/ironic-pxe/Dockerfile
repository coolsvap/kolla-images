FROM kollaglue/centos-binary-ironic-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)



RUN yum -y install \
        tftp-server \
        syslinux-tftpboot \
    && yum clean all



COPY tftp-map-file /map-file
COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start

