FROM kollaglue/centos-binary-cinder-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install \
        python-keystone \
  && yum clean all

    


COPY extend_start.sh /usr/local/bin/kolla_cinder_extend_start
RUN chmod 755 /usr/local/bin/kolla_cinder_extend_start



USER cinder