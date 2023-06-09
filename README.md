# network-observability

Installing Network Observability Operator


Installing Grafana Operator Community


Installing and Configuring Grafana Loki
* oc create -k manifests/loki/base

Deploy Grafana Dashboard
* oc create -k manifests/grafana-operator/overlays/instance/overlay

Deploy Network Observability
* oc create -k manifests/netobserv/instance/overlays/default/