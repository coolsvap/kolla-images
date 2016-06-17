FROM kollaglue/centos-binary-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)





RUN yum -y install \
        gcc \
        git \
        libffi-devel \
        libxml2-devel \
        libxslt-devel \
        MariaDB-devel \
        MariaDB-shared \
        openssl-devel \
        python-devel \
        openssh-clients \
    && yum clean all



RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py \
    && python get-pip.py \
    && rm get-pip.py \
    && pip --no-cache-dir install pytz \
    && pip --no-cache-dir install \
        'ansible>2' \
        MySQL-python \
        os-client-config==1.16.0 \
        pyudev \
        shade==1.4.0

RUN useradd -m --user-group ansible --groups kolla \
    && mkdir -p /etc/ansible /usr/share/ansible \
    && echo 'localhost ansible_connection=local' > /etc/ansible/hosts \
    && sed -i 's|  "identity_api_version": "2.0",|  "identity_api_version": "3",|' /usr/lib/python2.7/site-packages/os_client_config/defaults.json

COPY find_disks.py kolla_keystone_service.py kolla_keystone_user.py kolla_sanity.py kolla_zookeeper.py /usr/share/ansible/
COPY ansible.cfg /home/ansible/.ansible.cfg

CMD ["/bin/sleep", "infinity"]



USER ansible