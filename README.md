# OpenShift Image Handling & Monitoring/Alerting

Quick examples on using image streams, tags, image pull policies, Prometheus/AlertManager Rules, and cluster-/tenant-level monitoring & metrics.

# Additional Information

- Alerting for tenant projects:
  - https://docs.openshift.com/container-platform/4.6/monitoring/managing-alerts.html#accessing_the_alerting_ui_managing-alerts
  - https://docs.openshift.com/container-platform/4.6/monitoring/managing-alerts.html#Optimizing-alerting-for-user-defined-projects_managing-alerts
  - https://docs.openshift.com/container-platform/4.6/monitoring/managing-alerts.html#creating-alerting-rules-for-user-defined-projects_managing-alerts
  - [Configure alerting for:](https://docs.openshift.com/container-platform/4.6/monitoring/managing-alerts.html#configuring-alert-receivers_managing-alerts)
    - Email
    - Slack
- Grafana for tenant projects (optional):
  - https://access.redhat.com/solutions/5335491
  - Note this would require a standalone Prometheus/Thanos instance OR the cluster monitoring view role for cluster metrics, which opens up metrics viewing across all namespaces
  - Sample PromQL for a panel to limit by NS:

```
sum(node_namespace_pod_container:container_cpu_usage_seconds_total:sum_rate{namespace=~"cafe|alpha-httpbin"}) by (namespace)
```
