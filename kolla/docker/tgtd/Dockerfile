FROM kollaglue/centos-binary-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)



RUN yum -y install \
        scsi-target-utils \
    && yum clean all

RUN sed -i '1 i include /var/lib/cinder/volumes/*' /etc/tgt/tgtd.conf



