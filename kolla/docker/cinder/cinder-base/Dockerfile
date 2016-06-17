FROM kollaglue/centos-binary-openstack-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install \
        openstack-cinder \
        python-automaton \
        lvm2 \
        ceph-common \
    && yum clean all \
    && mkdir -p /etc/ceph

    


COPY cinder_sudoers /etc/sudoers.d/cinder_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN usermod -a -G kolla cinder \
    && chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/cinder_sudoers \
    && touch /usr/local/bin/kolla_cinder_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_cinder_extend_start