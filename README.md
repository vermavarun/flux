# flux
All operations for flux with Kubernetes

- Create cluster
  - kind create cluster --name flux-cluster
- show all clusters
  - kind get clusters
- Delete cluster
  - kind delete cluster
- Interact with new kind cluster
  - kubectl cluster-info --context flux-cluster


# Cluster
kubectl cluster-info --context kind-flux-cluster