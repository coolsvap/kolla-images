FROM kollaglue/centos-binary-neutron-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)



COPY neutron_sudoers /etc/sudoers.d/neutron_sudoers
COPY extend_start.sh /usr/local/bin/kolla_neutron_extend_start
RUN chmod 755 /usr/local/bin/kolla_neutron_extend_start \
    && chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/neutron_sudoers \
    && usermod -a -G kolla neutron



USER neutron