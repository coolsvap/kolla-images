FROM centos:7
MAINTAINER Kolla Project (https://launchpad.net/kolla)

LABEL kolla_version="3.0.0"



ENV KOLLA_BASE_DISTRO centos
ENV KOLLA_INSTALL_TYPE binary
ENV KOLLA_INSTALL_METATYPE rdo

#### Customize PS1 to be used with bash shell
COPY kolla_bashrc /tmp/
RUN cat /tmp/kolla_bashrc >> /etc/skel/.bashrc
RUN cat /tmp/kolla_bashrc >> /root/.bashrc

# PS1 var when used /bin/sh shell
ENV PS1="$(tput bold)($(printenv KOLLA_SERVICE_NAME))$(tput sgr0)[$(id -un)@$(hostname -s) $(pwd)]$ "

# For RPM Variants, enable the correct repositories - this should all be done
# in the base image so repos are consistent throughout the system.  This also
# enables to provide repo overrides at a later date in a simple fashion if we
# desire such functionality.  I think we will :)



RUN if [ $(awk '{match($0, /[0-9]+/,version)}END{print version[0]}' /etc/system-release) != "7" ]; then \
        echo "Only supported 7 release on centos"; false; fi

# Customize PS1 bash shell
RUN cat /tmp/kolla_bashrc >> /etc/bashrc

#### BEGIN REPO ENABLEMENT
# Turns on Elasticsearch repos
COPY elasticsearch.yum.repo /etc/yum.repos.d/elasticsearch.repo

# Turns on Kibana repo
COPY kibana.yum.repo /etc/yum.repos.d/kibana.yum.repo

# Turns on MariaDB repos throughout the RPM build
COPY mariadb.yum.repo /etc/yum.repos.d/MariaDB.repo

RUN yum -y install \
        http://repo.percona.com/release/7/RPMS/x86_64/percona-release-0.1-3.noarch.rpm

RUN rpm --import http://yum.mariadb.org/RPM-GPG-KEY-MariaDB \
    && rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-Percona \
    && rpm --import https://packages.elastic.co/GPG-KEY-elasticsearch

    


RUN curl http://trunk.rdoproject.org/centos7/current-passed-ci/delorean.repo -o /etc/yum.repos.d/delorean.repo

RUN curl http://trunk.rdoproject.org/centos7/delorean-deps.repo -o /etc/yum.repos.d/delorean-deps.repo


    
    

    

    

RUN rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7 \
    && yum -y install \
           epel-release \
           yum-plugin-priorities \
           centos-release-ceph-hammer \
           centos-release-qemu-ev \
    && rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7 \
    && rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-SIG-Storage \
    && rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-SIG-Virtualization \
    && yum clean all

    
    

    
    

    
    

    
    

#### END REPO ENABLEMENT



RUN yum -y update \
    && yum clean all

# Pin package versions
RUN yum -y install \
        yum-plugin-versionlock \
    && yum clean all
COPY versionlock.list /etc/yum/pluginconf.d/

    

# Install base packages
RUN yum -y install \
        sudo \
        which \
        python \
        lvm2 \
        scsi-target-utils \
        iscsi-initiator-utils \
    && yum clean all

    
    

    
    



COPY set_configs.py /usr/local/bin/kolla_set_configs
COPY start.sh /usr/local/bin/kolla_start
COPY sudoers /etc/sudoers
COPY curlrc /root/.curlrc
RUN touch /usr/local/bin/kolla_extend_start \
    && chmod 755 /usr/local/bin/kolla_start /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_set_configs \
    && chmod 440 /etc/sudoers \
    && groupadd kolla

RUN rm -f /tmp/kolla_bashrc

CMD ["kolla_start"]