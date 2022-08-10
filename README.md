# Unitest
Repository for Universe test case

## Install Prometheus
```shell
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm upgrade -if prometheus-values.yaml prometheus prometheus-community/prometheus -n unitest --create-namespace
helm upgrade -i prometheus-blackbox-exporter prometheus-community/prometheus-blackbox-exporter -n unitest
```

## Add secret with Grafana password
```shell
kubectl apply -f grafana-admin-secret.yaml -n unitest
```

## Install Grafana
```shell
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
helm upgrade -if grafana-values.yaml grafana grafana/grafana -n unitest
```

## Add configmap with Grafana dashboard
```shell
kubectl apply -f blackbox-exporter-cm.yaml -n unitest
```
