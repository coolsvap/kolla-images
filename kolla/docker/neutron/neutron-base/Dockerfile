FROM kollaglue/centos-binary-openstack-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install \
        openstack-neutron \
        openstack-neutron-ml2 \
        openvswitch \
        openstack-neutron-lbaas \
    && yum clean all

    


COPY neutron_sudoers /etc/sudoers.d/neutron_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN usermod -a -G kolla neutron \
    && chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/neutron_sudoers \
    && touch /usr/local/bin/kolla_neutron_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_neutron_extend_start