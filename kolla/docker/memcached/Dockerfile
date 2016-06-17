FROM kollaglue/centos-binary-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)




RUN yum -y install \
        memcached \
    && yum clean all \
    && usermod -a -G kolla memcached





USER memcached