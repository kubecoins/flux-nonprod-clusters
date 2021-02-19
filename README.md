# Flux non-production clusters

Represents the cluster state for non-production clusters

## Usage

Install Flux2

Set the following environment variables:

```bash
export GITHUB_TOKEN=<your-token>
export GITHUB_USER=<your-username>
```

Create your dev cluster using Cluster API (see *****) or locally using kind:

```bash
kind create cluster --name=kubecoins-dev
```

Check Flux2 pre-reqs:

```bash
flux check --pre
```

Bootstrap Flux for dev (if using CAPI change the context name):

```bash
flux bootstrap github \
    --context=kind-kubecoins-dev \
    --owner=${GITHUB_USER} \
    --repository=flux-nonprod-clusters \
    --branch=main \
    --personal \
    --path=clusters/dev
```

## Acknowledgments
This is based on this [Flux2 sample](https://github.com/fluxcd/flux2-kustomize-helm-example) and the **GitOps at Scale** work from Weaveworks.
