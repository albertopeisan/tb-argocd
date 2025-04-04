```bash
# Forward ClickHouse service to respective local port
kubectl port-forward svc/clickhouse 8123:8123 -n clickhouse
```
