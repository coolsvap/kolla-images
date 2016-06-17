FROM kollaglue/centos-binary-openstack-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install \
        openstack-sahara-common \
    && yum clean all

    



RUN usermod -a -G kolla sahara