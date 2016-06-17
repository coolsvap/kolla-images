FROM kollaglue/centos-binary-heat-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install \
        openstack-heat-api \
    && yum clean all

    


COPY extend_start.sh /usr/local/bin/kolla_heat_extend_start
RUN chmod 755 /usr/local/bin/kolla_heat_extend_start



USER heat