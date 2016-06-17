FROM kollaglue/centos-binary-designate-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

# The bind9 package here is only to provide the rndc binary.
RUN yum -y install \
        bind \
        openstack-designate-pool-manager \
    && yum clean all

    




USER designate