## 1. Добавляем helm repo

```bash

helm repo add jetstack https://charts.jetstack.io
helm repo update
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.10.1/cert-manager.crds.yaml
helm install   cert-manager jetstack/cert-manager   --namespace cert-manager   --create-namespace   --version v1.10.1 

helm repo add actions-runner-controller https://actions-runner-controller.github.io/actions-runner-controller
helm upgrade --install --namespace actions-runner-system --create-namespace\
  --set=authSecret.create=true\
  --set=authSecret.github_token="-"\
  --wait actions-runner-controller actions-runner-controller/actions-runner-controller

```

## 2. Запуск runner в кластере

```bash
kubectl apply -f runnerdeployment.yaml
```













