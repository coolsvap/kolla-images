FROM kollaglue/centos-binary-neutron-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

# Install required packages
RUN yum -y install \
        ebtables \
        openstack-neutron-linuxbridge \
    && yum clean all

    




USER neutron