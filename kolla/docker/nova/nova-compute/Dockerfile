FROM kollaglue/centos-binary-nova-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install \
        openstack-nova-compute \
        openvswitch \
        sysfsutils \
        ceph-common \
        genisoimage \
        iscsi-initiator-utils \
        targetcli \
        python-rtslib \
    && yum clean all

    


COPY extend_start.sh /usr/local/bin/kolla_nova_extend_start
RUN chmod 755 /usr/local/bin/kolla_nova_extend_start \
    && rm -f /etc/machine-id

ENV PATH $PATH:/lib/udev



USER nova