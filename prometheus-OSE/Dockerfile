FROM ubuntu:14.04
RUN  apt-get update \
  && apt-get install -y python-neutronclient python-novaclient python-keystoneclient python-netaddr unzip python-pip python-dev python-yaml \
  && pip install prometheus_client
COPY /prometheus-openstack-exporter/prometheus-openstack-exporter.yaml /etc/prometheus/
COPY /prometheus-openstack-exporter/prometheus-openstack-exporter.conf /etc/init
COPY admin.novarc /etc/prometheus-openstack-exporter/admin.novarc
COPY /prometheus-openstack-exporter/prometheus-openstack-exporter.service /etc/systemd/system/
COPY /prometheus-openstack-exporter/prometheus-openstack-exporter /prometheus-openstack-exporter
RUN  sh -c 'echo "NOVARC=/etc/prometheus-openstack-exporter/admin.novarc">/etc/default/prometheus-openstack-exporter'
RUN  sh -c 'echo "CONFIG_FILE=/etc/prometheus-openstack-exporter/prometheus-openstack-exporter.yaml">/etc/default/prometheus-openstack-exporter'
ENV  OS_USERNAME admin
ENV  OS_PASSWORD admin
ENV  OS_AUTH_URL http://172.24.3.2:35357/v2.0/
ENV  OS_AUTH_STRATEGY  keystone
ENV  OS_REGION_NAME  RegionOne
ENV  CINDER_ENDPOINT_TYPE  publicURL
ENV  GLANCE_ENDPOINT_TYPE  publicURL
ENV  KEYSTONE_ENDPOINT_TYPE  publicURL
ENV  NOVA_ENDPOINT_TYPE  publicURL
ENV  NEUTRON_ENDPOINT_TYPE  publicURL
ENV  OS_TENANT_NAME admin
RUN  mkdir -p /var/cache/prometheus-openstack-exporter
