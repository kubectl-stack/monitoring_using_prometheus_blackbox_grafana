##Install Blackbox Exporter

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
```
## Search repo blackbox it's add or not
```bash
helm search repo blackbox
```
## namespace given and it will created for that 
```bash
helm install blackbox prometheus-community/prometheus-blackbox-exporter --namespace monitoring --create-namespace 
```
## port-forward
```bash
kubectl port-forward <name of service cluster> -n <namespace> <local system port number>:<inside cluster port number>
```
