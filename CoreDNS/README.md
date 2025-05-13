# CoreDNS via kubeadm (for clusters installed using kubeadm)

##📥 2. Download the CoreDNS deployment manifest:
```bash
wget https://raw.githubusercontent.com/coredns/deployment/master/kubernetes/coredns.yaml.sed -O coredns.yaml.sed
```

## 🛠️ 3. Modify the coredns.yaml.sed (optional):
Replace ${CLUSTER_DNS_IP} with your Kubernetes cluster DNS IP (usually 10.96.0.10 for default kubeadm installs), and ${DNS_DOMAIN} with your cluster domain (usually cluster.local).
You can use sed like this:
```bash
sed -e 's/${CLUSTER_DNS_IP}/10.96.0.10/' -e 's/${DNS_DOMAIN}/cluster.local/' coredns.yaml.sed > coredns.yaml
```

##🚀 4. Apply the CoreDNS manifest:
```bash
kubectl apply -f coredns.yaml```

##🧪 Test DNS Resolution
```bash
kubectl run -i --tty --rm dns-test --image=busybox:1.28 --restart=Never -- nslookup kubernetes.default```


## Using helm (Advanced or Production Setup)
##📥 1. Add CoreDNS Helm repo:
```bash
helm repo add coredns https://coredns.github.io/helm
helm repo update
```
##🚀 2. Install CoreDNS via Helm:
```bash
helm install coredns coredns/coredns --namespace kube-system
```
##🧪 Test DNS Resolution

To verify that DNS resolution works:

```bash
kubectl run -i --tty --rm dns-test --image=busybox:1.28 --restart=Never -- nslookup kubernetes.default
```
## issue
```bash
Error from server (AlreadyExists): pods "dns-test" already exists
```

means that a pod named dns-test already exists in the cluster, likely from a previous 

To fix this 

```bash
kubectl delete pod dns-test
```
after than recreate that container for testing DNS



