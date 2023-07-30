# Helm Chart for Platform with ArgoCD Applications
This repository contains a Helm Chart for deploying a platform with ArgoCD Applications to manage the deployment of charts located in the charts directory.

## Prerequisites
Before proceeding with the installation, make sure you have the following tools installed:

- Helm - The package manager for Kubernetes.
- Kubernetes - The container orchestration platform.
- ArgoCD Installation
- Argo CD is a continuous delivery tool for Kubernetes. It helps to automate the deployment of applications to your Kubernetes cluster. To install ArgoCD, follow the steps below:

## Install ArgoCD using official website:

This installation was gotten from [official website](https://argo-cd.readthedocs.io/en/stable/getting_started/)

```bash 
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

You can find admin credential in argocd-initial-admin-secret K8s Secret resource or use command line.

```bash 
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

## Access the ArgoCD UI:

To access the ArgoCD UI, we will use port forwarding:

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

Open your browser and go to https://localhost:8080. Use admin as the username and the password obtained in the previous step to log in.

## Platform Installation using Helm
To deploy the platform along with ArgoCD Applications to manage charts in the charts directory, follow these steps:

Install the platform:

```bash
helm install <release-name> ./platform-chart
```

Replace <release-name> with the desired name for the release.
After this step you will have access to ArgoCD with Ingress. Use hostname which was specified in values.yaml.

## Additional Notes
Remember to update the Helm chart as needed when making changes to the platform or the ArgoCD Applications.
Make sure you have the appropriate Kubernetes RBAC permissions to deploy resources using ArgoCD.
## Troubleshooting
In case of any issues during the installation or deployment process, please refer to the official documentation of Helm and ArgoCD for further assistance.