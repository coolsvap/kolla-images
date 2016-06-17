FROM kollaglue/centos-binary-openvswitch-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)

COPY ovs_ensure_configured.sh /usr/local/bin/kolla_ensure_openvswitch_configured
COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_ensure_openvswitch_configured /usr/local/bin/kolla_extend_start

