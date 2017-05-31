FROM ubuntu:14.04
RUN  apt-get update \
  && apt-get install -y wget \
  && rm -rf /var/lib/apt/lists/* \
  && wget https://github.com/prometheus/prometheus/releases/download/v1.6.3/prometheus-1.6.3.linux-amd64.tar.gz \
  && tar xvf prometheus-1.6.3.linux-amd64.tar.gz
COPY prometheus.yml /prometheus-1.6.3.linux-amd64/prometheus.yml
