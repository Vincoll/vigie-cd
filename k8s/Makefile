# Deploy Vigie Demo

# DEV

apply-dev-standalone:
	kubectl apply --kustomize ./overlays/dev
	kubectl apply -f ./ingress/dev-ingress.yaml

delete-dev-standalone:
	kubectl delete --kustomize ./overlays/dev

# PRODUCTION STANDALONE

apply-prod-demo-standalone:
	kubectl apply --kustomize ./overlays/demo-standalone

delete-prod-demo-standalone:
	kubectl delete --kustomize ./overlays/demo-standalone

# PRODUCTION COMPLETE SIMPLE

apply-prod-demo-complete:
	kubectl apply --kustomize ./overlays/demo-complete
	kubectl apply -f ./ingress/demo-complete-ingress.yaml

delete-prod-demo-complete:
	kubectl delete --kustomize ./overlays/demo-complete


# INGRESS
apply-ingress:
	kubectl apply -f ./ingress/dev-ingress.yaml

delete-ingress:
	kubectl delete -f ./ingress/dev-ingress.yaml

# ====================================

force-deploy-demo: delete-k3d create-k3d k3d deploy-demo

deploy-dev: k3d
	kubectl apply --kustomize ./overlays/dev

deploy-demo: k3d
	kubectl apply --kustomize ./overlays/demo-standalone

export-config-demo: k3d
	kubectl kustomize --kustomize ./overlays/demo-standalone

delete-demo: k3d
	@kubectl delete --kustomize ./overlays/demo-standalone

delete-dev: k3d
	@kubectl delete --kustomize ./overlays/dev

ls: k3d
	@kubectl get all -A

log: k3d
	@kubectl logs -l x=vigie -n vigie-demo-standalone -f

dp: k3d
	@kubectl delete pod -l x=vigie -n vigie-demo-standalone


recreate-k3d: delete-k3d create-k3d

delete-k3d:
	@k3d delete --name vigie

create-k3d:
	@k3d create --name vigie

k3d:
	@export KUBECONFIG="$$(k3d get-kubeconfig --name=vigie)"

# /home/vincoll/.config/k3d/vigie/kubeconfig.yaml