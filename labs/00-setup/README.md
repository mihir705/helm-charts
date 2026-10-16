# Lab 00 — Setup

```bash
brew install helm kubectl
helm version
kubectl version --client

# Local cluster (any one)
# kind create cluster --name helm-lab
# or minikube start
```

`helm template` does not need a cluster. `helm install` does.
