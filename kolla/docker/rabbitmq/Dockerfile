FROM kollaglue/centos-binary-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)



RUN yum -y install \
        hostname \
        https://github.com/rabbitmq/rabbitmq-server/releases/download/rabbitmq_v3_5_7/rabbitmq-server-3.5.7-1.noarch.rpm \
    && yum clean all



# NOTE(sdake): the /bin/true unblocks the rabbitmq-plugins tool. Not sure how
#              or why.  My suspicion is it sends a signal to the parent
#              process.
RUN rm -rf /var/lib/rabbitmq/* \
    && curl -o /usr/lib/rabbitmq/lib/rabbitmq_server-3.5.7/plugins/rabbitmq_clusterer-3.5.x-189b3a81.ez http://www.rabbitmq.com/community-plugins/v3.5.x/rabbitmq_clusterer-3.5.x-189b3a81.ez \
    && /usr/lib/rabbitmq/bin/rabbitmq-plugins enable --offline \
       rabbitmq_management \
       rabbitmq_clusterer \
    && /bin/true

COPY extend_start.sh /usr/local/bin/kolla_extend_start
COPY rabbitmq_sudoers /etc/sudoers.d/rabbitmq_sudoers
COPY rabbitmq_get_gospel_node.py /usr/local/bin/rabbitmq_get_gospel_node
RUN chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/rabbitmq_get_gospel_node \
    && chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/rabbitmq_sudoers \
    && usermod -a -G kolla rabbitmq



USER rabbitmq