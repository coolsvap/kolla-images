FROM kollaglue/centos-binary-openstack-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

RUN yum -y install \
        openstack-dashboard \
        httpd \
        mod_wsgi \
        gettext \
    && yum clean all \
    && useradd --user-group horizon \
    && sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && ln -s /usr/share/openstack-dashboard/openstack_dashboard /usr/lib/python2.7/site-packages/openstack_dashboard \
    && ln -s /usr/share/openstack-dashboard/static /usr/lib/python2.7/site-packages/static \
    && chown -R horizon: /etc/openstack-dashboard /usr/share/openstack-dashboard \
    && chown -R apache: /usr/share/openstack-dashboard/static

RUN sed -i "s|WEBROOT = '/dashboard/'|WEBROOT = '/'|" /etc/openstack-dashboard/local_settings \
    && cp /usr/share/openstack-dashboard/manage.py /usr/bin/manage.py \
    && /usr/bin/python /usr/bin/manage.py collectstatic --noinput --clear \
    && (cd /usr/lib/python2.7/site-packages/horizon && /usr/bin/python /usr/bin/manage.py compilemessages) \
    && (cd /usr/lib/python2.7/site-packages/openstack_dashboard && /usr/bin/python /usr/bin/manage.py compilemessages)

    


COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start

