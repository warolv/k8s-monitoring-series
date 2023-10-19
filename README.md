# Monitoring with Kubernetes series

![monitoring-k8s](images/prometheus-operator/0.png)

  * Prometheus Operator
  * Grafana
  * Alert Manager
  * PushGateway
  * Thanos
  * Loki


## Prerequisite

### Create kind cluster

```bash
kind create cluster --image kindest/node:v1.23.1 --config ./kind/prometheus-config.yaml
```

### Install robo-shop

```bash
kubectl create ns robot-shop
helm install robot-shop --namespace robot-shop ./robot-shop/helm
```

### Install kube-prometeus-stack (prometheus operator)

```bash
helm install --wait --timeout 15m \
  --namespace monitoring --create-namespace \
  --repo https://prometheus-community.github.io/helm-charts \
  kube-prometheus-stack kube-prometheus-stack --values - <<EOF
kubeEtcd:
  service:
    targetPort: 2381
EOF
```

## Monitoring with k8s Posts
1. kube prometheus stack: install and overview of useful alerts and dashboards

2. Prometheus Operator: Scrape metrics from your application
    ServiceMonitor
    PodMonitor
    ScrapeConfig 
    ProbeMonitor

3. Prometheus Operator: Create alerts for your application  
   Prometheus Rule CRD

4.

5.

6.

7.

8.