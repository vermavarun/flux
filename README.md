# flux
All operations for flux with Kubernetes

- cluster-name: flux-cluster

<hr/>

- Create cluster
  - kind create cluster --name flux-cluster
- show all clusters
  - kind get clusters
- Delete cluster
  - kind delete cluster --name {cluster-name}
- Interact with new kind cluster
  - kubectl cluster-info --context flux-cluster


# Cluster
- kubectl cluster-info --context kind-flux-cluster
- kubectl config use-context {context-name} # to change context


# Flux

- flux get kustomizations --watch
- flux reconcile kustomization app-source --with-source
- flux -n flux-system create secret git git-access-auth --url=https://github.com/vermavarun/flux-source --username=vermavarun --password={PAT}

## set up local repo for flux tool

export GITHUB_USER=vermavarun
export GITHUB_TOKEN=''

`flux bootstrap github --owner=$GITHUB_USER --repository=flux --branch=main --path=./clusters/flux-cluster --personal`


## set up source of truth repo folder

`
flux create source git app-source --url=https://github.com/vermavarun/flux-source.git --branch=main --interval=30s --export > ./app-source/flux_source.yaml
`

## set up sync of truth repo

`
flux create kustomization app-source --target-namespace=default --source=app-source --path="./app" --prune=true --wait=true --interval=30m --retry-interval=2m --health-check-timeout=3m --export > ./clusters/flux-cluster/app-source-kustomization.yaml
`

run
`
kubectl apply -f deploy-app/flux_source.yaml
kubectl apply -f deploy-app/flux_sync.yaml
`


## deploy flux source of truth repo and sync

`

`

# Appendix

- [flux docs](https://fluxcd.io/flux/get-started/)
