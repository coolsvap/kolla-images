FROM kollaglue/centos-binary-nova-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)



RUN yum -y install \
        openssh-server \
    && yum clean all



COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start

