FROM kollaglue/centos-binary-nova-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install \
        openstack-nova-network \
        bridge-utils \
        initscripts \
    && yum clean all

    




USER nova