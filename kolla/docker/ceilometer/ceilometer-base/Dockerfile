FROM kollaglue/centos-binary-openstack-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install \
        openstack-ceilometer-common \
        python-tooz \
        python-oslo-db \
    && yum clean all

    



COPY ceilometer_sudoers /etc/sudoers.d/ceilometer_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN usermod -a -G kolla ceilometer \
    && chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/ceilometer_sudoers \
    && touch /usr/local/bin/kolla_ceilometer_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_ceilometer_extend_start