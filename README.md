# DevOps Assignment

## Provision EKS Cluster

```bash
cd terraform
terraform init
terraform apply
```

## Setup ArgoCD

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl port-forward svc/argocd-server -n argocd 8080:443
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

## Deploy NGINX

```bash
kubectl apply -f manifests/
```

## ArgoCD Application

```bash
kubectl apply -f argocd/nginx-app.yaml
```

## Access NGINX

```bash
kubectl get svc nginx-service
kubectl port-forward svc/nginx-service 8080:80
```