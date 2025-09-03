## Blackbox/VictoriaLogs
To use VictoriaLogs with Blackbox Exporter probes (such as HTTP probes) outside Kubernetes, the typical flow is:

Blackbox Exporter runs probes on targets and exports Prometheus-format metrics.

VMAgent scrapes these Blackbox Exporter probe metrics via its HTTP /probe endpoint.

VictoriaLogs collects logs from VMAgent or Blackbox Exporter for rich querying.

- https://github.com/prometheus/blackbox_exporter
- https://medium.com/trendyol-tech/probing-endpoints-with-blackbox-exporter-how-why-4417fce0993a
- https://www.opsramp.com/guides/prometheus-monitoring/prometheus-blackbox-exporter/

  
