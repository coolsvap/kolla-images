FROM kollaglue/centos-binary-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)

RUN useradd -r -m --user-group kibana \
    && usermod -a -G kolla kibana



RUN yum -y install \
        kibana \
    && yum clean all





USER kibana