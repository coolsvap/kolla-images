FROM kollaglue/centos-binary-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)



RUN yum -y install \
        mongodb \
        mongodb-server \
    && yum clean all



RUN mkdir -p /var/lib/mongodb /home/mongodb \
    && chown -R mongodb: /var/lib/mongodb /home/mongodb

COPY mongodb_sudoers /etc/sudoers.d/mongodb_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN usermod -a -G kolla mongodb \
    && chmod 755 /usr/local/bin/kolla_extend_start \
    && chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/mongodb_sudoers



USER mongodb