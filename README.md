## Install Grafana/Prometheus

I suggest using kube-prometheus-stack as it is the simplest way to get Prometheus and grafana running with awesome preinstalled dashboard for k8s monitoring:

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
```
##You can choose custom release name instead of 'prom'
if namespace not created than use this command

```bash
helm install prom prometheus-community/kube-prometheus-stack --namespace monitoring --create-namespace -f values.yaml
```
if namespace already have

```bash
helm install prom prometheus-community/kube-prometheus-stack -f values.yaml
```
check values.yaml
## port-forward

```bash
kubectl port-forward <service name of cluster> -n <namespace> <localbase port>:<inside cluster port>

```
