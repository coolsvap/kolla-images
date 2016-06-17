FROM kollaglue/centos-binary-designate-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install \
        openstack-designate-sink \
        python-designateclient \
    && yum clean all

    




USER designate