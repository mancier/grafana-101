# Kube Prometheus Stack - Grafana 101
Hello there! I hope everything is okay!

This project have the objective to help others to study and understand more about Grafana stack, so for this, I create this repo that contains kube-prometheus-stack and an application to be used as source of data and example and other things.

## Startup
Before we start is important to reinforce, for this project we will need some applications installed and configured in your computer.
- kubectl
- helm
- minikube
- cri-o
- docker

### Create minikube cluster locally to deploy the application
```bash
minikube start --container-runtime cri-o --cpus 4 --kubernetes-version 1.30.8 --memory 4g --profile grafana-101
```

### Deploy kube-stack-prometheus
```bash
helm dependency build
helm install app . --values values.yaml
```

### Deploy tns-app
```bash
kubectl apply --filename tns-app/
```

### Enable port-forward to grafana
```bash
kubectl port-forward --address 0.0.0.0 service/app-grafana 3000:80
```
