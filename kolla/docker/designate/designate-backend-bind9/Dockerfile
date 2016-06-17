FROM kollaglue/centos-binary-designate-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install \
        bind \
    && yum clean all \
    && mkdir -p /var/lib/kolla/ \
    && cp -pr /var/named /var/lib/kolla/var-named

    




USER designate