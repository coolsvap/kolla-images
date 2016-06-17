FROM kollaglue/centos-binary-neutron-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

# Install required packages
RUN yum -y install \
        openstack-neutron-openvswitch \
        openvswitch \
    && yum clean all

    




USER neutron