FROM kollaglue/centos-binary-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)



RUN yum -y install \
        MariaDB-Galera-server \
        MariaDB-client \
        rsync \
        galera \
        socat \
        hostname \
        percona-xtrabackup \
        pv \
        tar \
        expect \
    && yum clean all \
    && rm -rf /var/lib/mysql/*



COPY mariadb_sudoers /etc/sudoers.d/mariadb_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start
COPY security_reset.expect /usr/local/bin/kolla_security_reset
RUN chmod 755 /usr/local/bin/kolla_extend_start \
    && chmod 755 /usr/local/bin/kolla_security_reset \
    && chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/mariadb_sudoers \
    && usermod -a -G kolla mysql



USER mysql