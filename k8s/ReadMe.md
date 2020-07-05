# Apply on K8s

Vigie deployement and Ingress are separated as ingress components should be different on your cluster.  
This deployement use [Kustomize](https://kustomize.io/), check examples in the Makefile. *Kustomize is built-in kubectl >= 1.14*

## Vigie

Deploy Vigie with these manifests.

### Makefile

* `deploy-demo-complete`
* `deploy-demo-standalone`

### Argo

You can use this repo in a GitOps way. FYI this repo is sync with [ArgoCD](https://argoproj.github.io/argo-cd/) and delivers the [Vigie Public Demo](https://vigie.dev/demo).

## Ingress

My own ingress config, yours will be different.

### Makefile

* `apply-ingress-*`
* `delete-ingress-*`

### Argo