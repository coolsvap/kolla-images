FROM kollaglue/centos-binary-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)



RUN yum -y install \
        https://github.com/mozilla-services/heka/releases/download/v0.10.0/heka-0_10_0-linux-amd64.rpm \
    && yum clean all \
    && useradd --user-group heka \
    && mkdir /etc/heka



COPY plugins/modules /usr/share/heka/lua_modules/
COPY plugins/decoders /usr/share/heka/lua_decoders/
COPY plugins/encoders /usr/share/heka/lua_encoders/

COPY heka_sudoers /etc/sudoers.d/heka_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN usermod -a -G kolla heka \
    && chmod 440 /etc/sudoers.d/heka_sudoers \
    && chmod 755 /usr/local/bin/kolla_extend_start \
    && chown -R heka: /usr/share/heka /etc/heka



USER heka