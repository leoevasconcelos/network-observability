# network-observability

Installing Network Observability Operator


Installing Grafana Operator Community


Installing and Configuring Grafana Loki
* kubectl apply -k manifests/loki/base

Deploy Grafana Dashboard
* kubectl apply -k manifests/grafana-operator/overlays/instance/overlay

Deploy Network Observability
* kubectl apply -k manifests/netobserv/instance/overlays/default/# network-observability
