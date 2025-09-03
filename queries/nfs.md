
##### Check NFSv4 Client Operations/s	
`rate(node_nfs4_client_operations_total[5m])`

##### Check NFSv4 Server Operations/s	
`rate(node_nfs4_server_operations_total[5m])`

##### NFSv4 Average Read Latency	
`rate(node_nfs4_client_read_latency_seconds_sum[5m]) / rate(node_nfs4_client_read_latency_seconds_count[5m])`

##### NFSv4 Mount Errors	
`node_nfs4_mount_errors_total`

##### NFSv4 Operations Filtered by Exported Path	
`rate(node_nfs4_client_operations_total{exported_path="/mnt/nfs_share"}[5m])`

##### Port up status (e.g., NFS default port 2049)	
`up{instance=~".*:2049"}`

##### NFSv4 Operations on Specific Port	
`rate(node_nfs4_client_operations_total{port="2049"}[5m])`

##### NFSv4 Mount Errors on Specific Port	
`node_nfs4_mount_errors_total{port="2049"}`

##### Network traffic on Port 2049
`node_network_receive_bytes_total{port="2049"}`

##### General HTTP requests for VictoriaMetrics port	
`http_requests_total{instance=~":8428$"}`

##### Up status for VictoriaMetrics ports	
`up{instance=~":8481$"}`

##### Scrape duration for VictoriaMetrics 
`ports	scrape_duration_seconds{instance=~":8482$"}`

