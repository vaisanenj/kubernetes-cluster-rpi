# Monitoring Kuberentes Cluster with Prometheus and Grafana

For monitoring k8s cluster I found kube-prometheus project on [github](https://github.com/prometheus-operator/kube-prometheus) that is started using. It include all manifest files that are needed to run monitoring system. Currently i cloned 0.10 version manifest files in my project and added some change for my use. For example I updated grafana-service to LoadBalancer so I could access to grafana easier from outside of cluster.

## Setting Monitoring system up
1. `kubectl create -f ../monitoring/kube-prometheus-0.10/manifests/setup` First we need to create files from setup folder.
2. `kubectl create -f ../monitoring/kube-prometheus-0.10/manifests` After setup folder is run then we can run other manifest files.
3. `kubectl get all -n monitoring` Check that all resources are running corretly.
