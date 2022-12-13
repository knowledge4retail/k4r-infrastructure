# Monitoring Infrastructure

## Introduction

When running multiple applications on a Kubernetes cluster, you need to configure the monitoring infrastructure to be able to collect and view the metrics reporting the health and statistical information about your deployed applications.

This guide will show you how to install and configure the Prometheus and Grafana monitoring tools.

This setup uses the Prometheus/Grafana/Alertmanager/Kube-State-Metrics/Node Exporter to monitor the Kubernetes cluster.



[Prometheus](https://prometheus.io/), [Grafana](https://grafana.com/), [Alertmanager](https://www.prometheus.io/docs/alerting/latest/alertmanager/), [Kube-State-Metrics](https://github.com/kubernetes/kube-state-metrics) and [Node Exporter](https://prometheus.io/docs/guides/node-exporter/).

## Requirements

* access to a running kubernetes cluster
* docker, kubectl `>= v1.20.0` and helm `>= v3.6.3`   installed on your local machine
* the current `kubectl` context is pointing to the correct Kubernetes cluster
* the current namespace is set to the required namespace for the monitoring infrastructure
* the following instructions assume that you are running the commands on bash (or a similar shell)

## Setup

This setup is done by the following steps:

* Create Prometheus from the Helm chart.

### Install Prometheus with kube-prometheus-stack


``` shell
# Add Prometheus Helm repository
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

# update the local cache
helm repo update

# install Prometheus
helm install prometheus-monitoring prometheus-community/kube-prometheus-stack --version 31.0.0  --wait --debug --atomic
```

By default this chart installs additional, dependent charts:

prometheus-community/kube-state-metrics

prometheus-community/prometheus-node-exporter

grafana/grafana


## Accessing Prometheus

### Using port-forwarding

1. To connect to the Grafana UI run the following command: `kubectl port-forward svc/prometheus-monitoring-grafana 3000:80`

2. in browser, navigate to: `http://localhost:3000/`

3. enter the username and password for the Grafana user `admin` and click `Login`. (password can be found in the secret `prometheus-monitoring-grafana` under the key`admin-password`)

4. Dashboards can be created and edited or imported (e.g. MongoDB Dashboard, Postgresql Dashboard) in the Grafana UI `http://localhost:3000/dashboards`

Alternatively Grafana can be accessed by configuring the Ingress resource in the Helm chart.
See the official [Values.yaml](https://github.com/prometheus-community/helm-charts/blob/f21389ba4ad38d201ac71ff61223bc365b8c5238/charts/kube-prometheus-stack/values.yaml#L216)
