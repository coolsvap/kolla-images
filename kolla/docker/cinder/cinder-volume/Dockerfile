FROM kollaglue/centos-binary-cinder-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)



RUN yum -y install \
        scsi-target-utils \
    && yum clean all

RUN sed -i '1 i include /var/lib/cinder/volumes/*' /etc/tgt/tgtd.conf



COPY cinder_sudoers /etc/sudoers.d/cinder_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/cinder_sudoers \
    && chmod 755 /usr/local/bin/kolla_extend_start



USER cinder