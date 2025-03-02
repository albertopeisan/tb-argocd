# ArgoCD configuration

This repository contains the applications for app-of-apps pattern to create ArgoCD applications and projects.

## Prepare the argocd Kubernetes namespace

```bash
kubectl create namespace argocd
kubectl apply -f ./manifests/argocd/install.yaml -n argocd
```

## Retrieve argocd credentials and forward traffic

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

## Create argocd project and app-of-apps pattern

This project allows the argocd repository as a source and allows deploying AppProject and Application manifests to the argocd namespace.

```bash
kubectl apply -f ./projects/argocd.yaml
```

Create the projects ArgoCD Application, this will sync the projects directory in the repository.

```bash
kubectl apply -f ./applications/argocd/projects.yaml
```

Create the applications ArgoCD Application, this will sync the applications directory in the repository.

```bash
kubectl apply -f ./applications/argocd/applications.yaml
```

Perform a synchronization, the repository is now templated in argocd.

You can perform the following now:

- Add new applications under the `applications` directory.
- Add new projects under the `projects` directory.
- Add new helm chart values used in applications in the `charts` directory.
- Add new yaml manifests in the `manifests` directory. 