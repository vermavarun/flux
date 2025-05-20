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
- kubectl cluster-info --context kind-flux-cluster
- kubectl config use-context {context-name} # to change context


# Flux

## set up local repo

export GITHUB_USER=vermavarun
export GITHUB_TOKEN=''

`flux bootstrap github --owner=$GITHUB_USER --repository=flux --branch=main --path=deployinfra --personal`