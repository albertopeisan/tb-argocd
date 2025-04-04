```bash
# Forward Prometheus server service to respective local port
kubectl port-forward svc/prometheus-server 9090:9090 -n prometheus
```