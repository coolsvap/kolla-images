FROM kollaglue/centos-binary-murano-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install \
        openstack-murano-api \
    && yum clean all

    


COPY extend_start.sh /usr/local/bin/kolla_murano_extend_start
RUN chmod 755 /usr/local/bin/kolla_murano_extend_start



USER murano