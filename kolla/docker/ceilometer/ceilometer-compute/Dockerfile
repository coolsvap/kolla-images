FROM kollaglue/centos-binary-ceilometer-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install \
        openstack-ceilometer-compute \
        python-ceilometerclient \
    && yum clean all

    




USER ceilometer