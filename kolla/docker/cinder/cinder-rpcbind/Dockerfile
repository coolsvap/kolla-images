FROM kollaglue/centos-binary-cinder-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)



RUN yum -y install \
        nfs-utils \
        nfs-utils-lib \
    && yum clean all





USER cinder