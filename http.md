```yaml
Total HTTP requests counter
http_requests_total
HTTP requests per service (rate over 5 min)
rate(http_requests_total[5m]) by (service)

Last value of HTTP requests over time window
last_over_time(http_requests_total[15m])

Sum of HTTP requests over time window
sum(last_over_time(http_requests_total[15m])) by (service)

VictoriaMetrics HTTP API Query endpoint
/api/v1/query?query=<your_promql_query> (e.g., http_requests_total)

VictoriaLogs HTTP log query endpoint
/select/logsql/query with LogSQL query in post data (e.g., 'query=error')

Live tailing logs endpoint
/select/logsql/tail with LogSQL query in post data

Log field names query endpoint
/select/logsql/stream_field_names with query and timeframe

Log stats query at given time
/select/logsql/stats_query?query=<query>&time=<timestamp> returns logs stats metrics

Top running queries API
/api/v1/status/top_queries?topN=5&maxLifetime=30s
```
