## Blackbox/VictoriaLogs
Blackbox exporter generates metrics that depend on the response time of internal or external endpoints, such as HTTP/S, TCP, ICMP, DNS.

To use VictoriaLogs with Blackbox Exporter probes (such as HTTP probes) outside Kubernetes, the typical flow is:
  - Blackbox Exporter runs probes on targets and exports Prometheus-format metrics.
  - VMAgent scrapes these Blackbox Exporter probe metrics via its HTTP /probe endpoint.
  - VictoriaLogs collects logs from VMAgent or Blackbox Exporter for rich querying.

- https://github.com/prometheus/blackbox_exporter
- https://medium.com/trendyol-tech/probing-endpoints-with-blackbox-exporter-how-why-4417fce0993a
- https://www.opsramp.com/guides/prometheus-monitoring/prometheus-blackbox-exporter/
     
    

#### HTTP Module
```yaml
modules: 
  http_2xx: 
    http: 
      fail_if_not_ssl: true
      ip_protocol_fallback: false
      method: GET
      no_follow_redirects: false
      preferred_ip_protocol: ip4
      valid_http_versions: 
        - HTTP/1.1
        - HTTP/2.0
    prober: http
    timeout: 15s
```  
#### Defintion of Module
![screenshot](blackbox.png)


####  TCP Module
```yaml
modules: 
  tcp_connect: 
    prober: tcp
    tcp: 
      ip_protocol_fallback: false
      preferred_ip_protocol: ip4
      tls: true
      tls_config: 
        insecure_skip_verify: true
        server_name: myserver
    timeout: 15s
```

**NOTE:** Above config requires Prometheus scrape config to get the relevant metrics from the blackbox endpoint. 
```yaml
global:
  scrape_interval:     15s
  evaluation_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
    - targets: ['prometheus:9090', 'blackbox:9115']

  - job_name: 'blackbox'
    metrics_path: /probe
    params:
      module: [http_2xx]
    static_configs:
    - targets:
      - https://gitlab.com
      - https://morethancertified.com
      - https://nationarail.co.uk
      - https://lner.co.uk
      - https://twitter.com
      - https://theregister.com
      - https://web.archive.org
      - https://xe.com
      - https://youtube.com
      - https://yahoo.com
      # Add yours here....

    relabel_configs:
        - source_labels: [__address__]
          target_label: __param_target
        - source_labels: [__param_target]
          target_label: instance
        - target_label: __address__
          replacement: blackbox:9115  # Replace with the actual address where Blackbox Exporter is running

```

