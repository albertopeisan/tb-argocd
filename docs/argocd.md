Use this command to forward traffic from localhost to argocd.

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```
