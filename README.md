## network-observability

```bash
oc new-project netobserv
```

## Installing Network Observability Operator
![](images/operator_netobserv.png)

## Installing Grafana Operator Community
![](images/operator_grafana.png)

## Git Clone Project
```bash
git clone https://github.com/leoevasconcelos/network-observability.git
```

## Installing and Configuring Grafana Loki
```bash
oc create -k manifests/loki/base
```
Deploy Grafana Dashboard
```bash
oc create -k manifests/grafana-operator/overlays/instance/overlay
```
Deploy Network Observability Flow Collector
```bash
oc create -k manifests/netobserv/instance/overlays/default/
```

```bash
oc get flowcollector
```
## Netobserv Grafana Dashboards
![](images/netobserv-5.png)

## OpenShift Console Plugin
![](images/netobserv-6.png)

## Netword Traffic
![](images/netobserv-7.png)

## Flow Tables
![](images/netobserv-8.png)

## Network Traffic of some specific Pods
![](images/netobserv-9.png)


![](images/netobserv-10.png)


![](images/red.png)

[Link para documentação oficial Red Hat](https://docs.openshift.com/container-platform/4.10/networking/network_observability/network-observability-overview.html) 