```bash
# Forward ArgoCD service to respective local port
kubectl port-forward svc/argocd-server 8080:443 -n argocd
```
