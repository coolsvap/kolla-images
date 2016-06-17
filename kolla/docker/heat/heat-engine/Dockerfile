FROM kollaglue/centos-binary-heat-base:3.0.0
MAINTAINER Kolla Project (https://launchpad.net/kolla)


    

# TODO(SamYaple): until packaging is fixed, all of the python clients below are required
# http://pkgs.fedoraproject.org/cgit/openstack-heat.git/tree/openstack-heat.spec#n248
RUN yum -y install \
        python-barbicanclient \
        python-zaqarclient \
        openstack-heat-engine \
    && yum clean all

   




USER heat