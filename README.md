# ArgoCD configuration

This repository contains the applications for app-of-apps pattern to create ArgoCD applications and projects.

## Create argocd project

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

Perform a synchronization, the repository is now templated in ArgoCD.