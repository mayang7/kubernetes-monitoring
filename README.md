# kubernetes-monitoring

This repository contains a ready-to-import Grafana dashboard JSON for Kubernetes monitoring.

## Dashboard

- File: `kubernetes-monitoring-dashboard.json`
- Purpose: monitor Kubernetes cluster CPU, memory, pod restarts, disk utilization, and network throughput via Prometheus.

## Usage

1. Open Grafana.
2. Go to Dashboards > Import.
3. Upload `kubernetes-monitoring-dashboard.json`.
4. Select your Prometheus datasource or set the `DS_PROMETHEUS` variable.

> Make sure your Prometheus server exposes Kubernetes metrics such as `node_cpu_seconds_total`, `container_cpu_usage_seconds_total`, `container_memory_working_set_bytes`, `kube_pod_container_status_restarts_total`, and `node_filesystem_*`.
