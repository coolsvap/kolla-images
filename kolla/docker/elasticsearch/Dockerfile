FROM kollaglue/centos-binary-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)



ENV JAVA_HOME /usr/lib/jvm/jre-1.7.0-openjdk/

RUN yum -y install \
        java-1.7.0-openjdk \
        elasticsearch \
    && yum clean all



COPY elasticsearch_sudoers /etc/sudoers.d/elasticsearch_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start \
    && chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/elasticsearch_sudoers \
    && usermod -a -G kolla elasticsearch


# by default elasticsearch shell is /bin/false, we need
# /bin/bash to run elasticsearch as non-root
# https://discuss.elastic.co/t/running-as-non-root-user-service-wrapper-has-changed/7863
RUN usermod -s /bin/bash elasticsearch -d /usr/share/elasticsearch



USER elasticsearch