```yaml
Query DNS Request Count  (last minutes)
rate(dns_requests_total[5m])

Count DNS Errors
dns_errors_total

DNS Query Types Breakdown
sum by (query_type) (rate(dns_requests_total[5m]))

Shows counts of different DNS query types (A, AAAA, MX, etc.).

DNS Response Latency
rate(dns_response_duration_seconds_sum[5m]) / rate(dns_response_duration_seconds_count[5m])

DNS Cache Hit Ratio
(sum(rate(dns_cache_hits_total[5m])) / sum(rate(dns_requests_total[5m]))) * 100
```

