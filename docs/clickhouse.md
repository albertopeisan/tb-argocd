Use this command to forward traffic from localhost to clickhouse.

```bash
kubectl port-forward -n clickhouse svc/clickhouse \
  8123:8123 \
  9000:9000 \
  9004:9004 \
  9005:9005 \
  9009:9009
```
