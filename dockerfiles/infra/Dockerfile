FROM spredzy:infra-sshd
MAINTAINER Yanis Guenane <yanis@guenane.org>

RUN yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
RUN yum -y install http://yum.puppetlabs.com/puppetlabs-release-el-7.noarch.rpm && yum -y install wget git cronie

RUN wget -O /tmp/install_modules.sh https://raw.githubusercontent.com/openstack-infra/system-config/master/install_modules.sh; \
wget -O /tmp/install_puppet.sh https://raw.githubusercontent.com/openstack-infra/system-config/master/install_puppet.sh; \
wget -O /tmp/modules.env https://raw.githubusercontent.com/openstack-infra/system-config/master/modules.env; \
bash /tmp/install_puppet.sh; \
bash /tmp/install_modules.sh; \
git clone https://review.openstack.org/openstack-infra/system-config /tmp/system-config; \
cp -r /tmp/system-config/modules/openstack_project /etc/puppet/modules/

CMD ["/sbin/init"]
