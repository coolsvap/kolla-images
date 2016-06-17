FROM kollaglue/centos-binary-neutron-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)



RUN yum -y install \
        haproxy \
    && yum clean all




    

RUN yum -y install \
        openstack-neutron-lbaas \
    && yum clean all

    



COPY extend_start.sh /usr/local/bin/kolla_neutron_extend_start
RUN chmod 755 /usr/local/bin/kolla_neutron_extend_start



USER neutron