FROM kollaglue/centos-binary-openstack-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install \
        openstack-swift \
    && yum clean all

    


RUN pip install oslo.rootwrap

COPY swift-rootwrap /var/lib/kolla/venv/bin/swift-rootwrap
COPY rootwrap.conf /etc/swift/rootwrap.conf
RUN chmod 755 /var/lib/kolla/venv/bin/swift-rootwrap \
    && chmod 644 /etc/swift/rootwrap.conf \
    && sed -i 's|^exec_dirs.*|exec_dirs=/var/lib/kolla/venv/bin,/sbin,/usr/sbin,/bin,/usr/bin,/usr/local/bin,/usr/local/sbin|g' /etc/swift/rootwrap.conf

COPY swift_sudoers /etc/sudoers.d/swift_sudoers
RUN chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/swift_sudoers

COPY build-swift-ring.py /usr/local/bin/kolla_build_swift_ring
RUN mkdir -p /opt/swift

RUN usermod -a -G kolla swift