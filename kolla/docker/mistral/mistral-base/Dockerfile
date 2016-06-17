FROM kollaglue/centos-binary-openstack-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)



    

RUN yum -y install \
        openstack-mistral-common \
    && yum clean all

    



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN usermod -a -G kolla mistral \
    && touch /usr/local/bin/kolla_mistral_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_mistral_extend_start