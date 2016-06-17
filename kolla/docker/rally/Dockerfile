FROM kollaglue/centos-binary-openstack-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install \
        openstack-rally \
    && yum clean all \
    && useradd --user-group rally

    


RUN usermod -a -G kolla rally



USER rally