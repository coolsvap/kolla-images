FROM kollaglue/centos-binary-gnocchi-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install \
        openstack-gnocchi-api \
        openstack-gnocchi-carbonara \
        openstack-gnocchi-indexer-sqlalchemy \
    && yum clean all

    


COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start



USER gnocchi