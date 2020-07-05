# Vigie Continuous Deployment

The purpose this repo is to allow you to quickly and easily deploy Vigie and its components.

## K8s

This k8s deployement is used by the [Vigie Demo](https://vigie.dev/demo.html) with [ArgoCD](https://argoproj.github.io/argo-cd/)

The deployement is well structured, but do not include any security.  
Vigie is still in alpha state, secrets management are not my main concern.

| **Included**                                                                              | **Not Included**                  |
|-------------------------------------------------------------------------------------------|-----------------------------------|
| Quick start config<br>Wiring between services<br>  * Vigie<br>  * Grafana<br>  * InfluxDB <br> * Prometheus  | Data persistance<br>Security|  

## Start Deploy

**Standalone**

* Vigie Alone

**Complete**

* Vigie + Grafana + InfluxDB

*which mode to chose ? [(Doc)](https://docs.vigie.dev/configuration/modes/)*
