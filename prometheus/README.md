# Prometheus configuration

This directory contains a sample Prometheus configuration for Kubernetes service discovery.

## Usage

1. Mount `prometheus/prometheus.yml` into your Prometheus container or server config path.
2. Ensure Prometheus has permission to access the Kubernetes API server via a service account token.
3. Confirm the cluster has exporters or annotated pods for metrics collection:
   - `kube-state-metrics`
   - `node-exporter`
   - Cilium metrics endpoint
   - FRR/BGP exporter endpoint

## Recommended deployment

If you run Prometheus in Kubernetes, mount the config and token as follows:

```yaml
volumes:
  - name: prometheus-config
    configMap:
      name: prometheus-config
  - name: kube-api-access
    projected:
      sources:
        - serviceAccountToken:
            path: token
            expirationSeconds: 3600

volumeMounts:
  - name: prometheus-config
    mountPath: /etc/prometheus/prometheus.yml
    subPath: prometheus.yml
  - name: kube-api-access
    mountPath: /var/run/secrets/kubernetes.io/serviceaccount
```
