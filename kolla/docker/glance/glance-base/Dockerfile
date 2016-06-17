FROM kollaglue/centos-binary-openstack-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install \
        openstack-glance \
        python-rbd \
        python-rados \
    && yum clean all \
    && mkdir -p /etc/ceph/

    


COPY glance_sudoers /etc/sudoers.d/glance_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN usermod -a -G kolla glance \
    && chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/glance_sudoers \
    && touch /usr/local/bin/kolla_glance_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_glance_extend_start