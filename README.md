# argocd-helm

## install ArgoCD in k8s
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
## access ArgoCD UI
```
kubectl get svc -n argocd
kubectl port-forward svc/argocd-server 8282:443 -n argocd
```
## login with admin user and below token (as in documentation):

```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 --decode && echo

kubectl get secret argocd-initial-admin-secret -n argocd -o yaml
```
## deploy argocd helm app

```
kubectl apply -f application.yaml
```

## accessing app using port forward

```
kubectl port-forward -n helm-chart svc/nginxservice 80:80
```
