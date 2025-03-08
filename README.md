# Configuring ArgoCD

This repository is designed to hold all the applications, projects, Helm charts, configurations, and other resources for managing your Kubernetes cluster. It serves as a centralized location for everything related to your Kubernetes environment.

This repository uses the **app-of-apps pattern** to create ArgoCD applications and projects:

- The `applications/argocd/applications.yaml` manifest creates all the applications inside the `applications` directory.

- The`applications/argocd/projects.yaml` manifest creates all the projects inside the `projects` directory.

## Table of Contents

- [Repository Structure](#repository-structure)
- [Configuring ArgoCD](#configuring-argocd)

## Repository Structure

The repository is organized into the following directories:

```
my-kubernetes-repo/
├── applications/
│   ├── app1/
│   │   ├── deployment.yaml
│   │   ├── service.yaml
│   │   └── ...
│   ├── app2/
│   │   ├── deployment.yaml
│   │   ├── service.yaml
│   │   └── ...
│   └── ...
├── charts/
│   ├── chart1/
│   │   ├── Chart.yaml
│   │   ├── values.yaml
│   │   ├── templates/
│   │   └── ...
│   ├── chart2/
│   │   ├── Chart.yaml
│   │   ├── values.yaml
│   │   ├── templates/
│   │   └── ...
│   └── ...
├── docs/
│   └── ...
├── manifests/
│   └── ...
├── projects/
│   └── ...
└── README.md
```

- **`applications/`**: Contains the ArgoCD Kubernetes manifests for each application.
- **`charts/`**: Contains Helm charts for deploying applications.
- **`docs/`**: Contains documentation about the repository.
- **`manifests/`**: Contains yaml manifests to deploy applications.
- **`projects/`**: Contains the ArgoCD Kubernetes manifests for each project.

## Configuring ArgoCD

### Pre-requisites

- A kubernetes cluster running with ArgoCD installed.

## Create argocd repository and argocd project

Create the `argocd` project that allows this repository as a source and `argocd` as destination namespace.

```bash
kubectl apply -f ./projects/argocd.yaml
```

Create the `projects` Application, this will sync the `projects` directory in the repository.

```bash
kubectl apply -f ./applications/argocd/projects.yaml
```

Go to ArgoCD UI and sync all the projects application manually before proceeding.

Create the `applications` Application, this will sync the `applications` directory in the repository.

```bash
kubectl apply -f ./applications/argocd/applications.yaml
```

Perform a synchronization, the repository is now templated in argocd.

You can perform the following now:

- Add new applications under the `applications` directory.
- Add new projects under the `projects` directory.
- Add new helm chart values used in applications in the `charts` directory.
- Add new yaml manifests in the `manifests` directory. 