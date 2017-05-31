# PrometheusSetup
Setup Prometheus and OpenstStack exporter

File list
prometheus-server/Dockerfile -  dockerfile to create prometheus docker container
prometheus-server/Dockerfile -  dockerfile to create prometheus OpenStack explore docker container

Usage:
git clone https://github.com/lenovo/PrometheusSetup.git
cd prometheus-OSE
git clone https://github.com/CanonicalLtd/prometheus-openstack-exporter.git
updata the ip and password at admin.novarc
docker build -t prometheus_ose.
docker run  -d -p 9183:9183  ./prometheus-openstack-exporter /etc/prometheus/prometheus-openstack-exporter.yaml
cd prometheus-server
docker build -t prometheus .
docker run -d  prometheus  ./prometheus-1.6.3.linux-amd64/prometheus -config.file=/prometheus-1.6.3.linux-amd64/prometheus.yml


