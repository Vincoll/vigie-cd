# Deploy Vigie Demo

# DEV

deploy-dev: apply-dev apply-ingress-dev

apply-dev:
	kubectl apply --kustomize ./overlays/dev

delete-dev:
	kubectl delete --kustomize ./overlays/dev

# PRODUCTION STANDALONE

deploy-demo-standalone: apply-demo-standalone apply-ingress-demo-complete

apply-demo-standalone:
	kubectl apply --kustomize ./overlays/demo-standalone

delete-demo-standalone:
	kubectl delete --kustomize ./overlays/demo-standalone

# PRODUCTION COMPLETE SIMPLE

deploy-demo-complete: apply-demo-complete apply-ingress-demo-complete

apply-demo-complete:
	kubectl apply --kustomize ./overlays/demo-complete

delete-demo-complete:
	kubectl delete --kustomize ./overlays/demo-complete


# INGRESS

apply-ingress-dev:
	kubectl apply --kustomize ./ingress/overlays/dev

apply-ingress-demo-complete:
	kubectl apply --kustomize ./ingress/overlays/demo-complete

delete-ingress-demo-complete:
	kubectl delete --kustomize ./ingress/overlays/demo-complete

delete-ingress-dev:
	kubectl delete --kustomize ./ingress/overlays/ingress-dev



# ====================================
# LOCAL
# ====================================

force-deploy-dev: delete-k3d create-k3d k3d deploy-dev
force-deploy-demo: delete-k3d create-k3d k3d deploy-demo-complete

deploy-local-dev: k3d
	kubectl apply --kustomize ./overlays/dev
	kubectl apply -f ./ingress/local-ingress.yaml

deploy-local-demo: k3d
	kubectl apply --kustomize ./overlays/demo-complete

apply-ingress-dev:
	kubectl apply -f ./ingress/local-ingress.yaml

export-config-demo: k3d
	kubectl kustomize --kustomize ./overlays/demo-standalone

delete-demo: k3d delete-demo-complete

delete-dev: k3d delete-dev

ls: k3d
	@kubectl get all -A

log: k3d
	@kubectl logs -l x=vigie -n vigie-demo-standalone -f

dp: k3d
	@kubectl delete pod -l x=vigie -n vigie-demo-standalone

recreate-k3d: delete-k3d create-k3d

delete-k3d:
	@k3d delete --name localvigie

create-k3d:
	@k3d create --name localvigie --api-port localhost:6444 --publish 8080:80 --server-arg --tls-san="127.0.0.1"

k3d:
	@export KUBECONFIG="$$(k3d get-kubeconfig --name=localvigie)"
	@cp $$(k3d get-kubeconfig --name=localvigie) $$HOME/.kube/k3d-localvigie-config.yaml
