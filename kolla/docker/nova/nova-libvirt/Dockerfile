FROM kollaglue/centos-binary-nova-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)





RUN yum -y install \
        libvirt-daemon \
        libguestfs \
        qemu-system-x86 \
        libvirt-daemon-driver-nwfilter \
        libvirt-daemon-config-nwfilter \
        libvirt-daemon-driver-lxc \
        ceph-common \
    && yum clean all \
    && usermod -a -G nova qemu




COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start

