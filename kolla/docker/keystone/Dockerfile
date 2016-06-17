FROM kollaglue/centos-binary-openstack-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install openstack-keystone \
        python-keystoneclient \
        httpd \
        mod_wsgi \
    && yum clean all

RUN mkdir -p /var/www/cgi-bin/keystone \
    && cp -a /usr/share/keystone/keystone.wsgi /var/www/cgi-bin/keystone/main \
    && cp -a /usr/share/keystone/keystone.wsgi /var/www/cgi-bin/keystone/admin \
    && sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf

    


RUN usermod -a -G kolla keystone \
    && chown -R keystone: /var/www/cgi-bin/keystone \
    && chmod 755 /var/www/cgi-bin/keystone/*

COPY keystone_bootstrap.sh /usr/local/bin/kolla_keystone_bootstrap
COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_keystone_bootstrap

