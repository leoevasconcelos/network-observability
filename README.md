# OpenShift 4 Network Observability

# How can we analyze our Network Flows in our Kubernetes clusters? How can we enable Network Observability for Kubernetes in a simple, searchable and visual way? How can we leverage cool technologies such as eBPF or IPFIX to enable Network Observability for our K8s Network Traffic?

```bash
oc new-project netobserv
```
# 1 - Installing NetObserv Operator Prerequisites

![OpenShift NetObservability Operator](images/gitops-01.png)

# 2 - Installing Grafana Operator and Deploy a Grafana instance for NetObserv

![OpenShift Grafana Operator](images/gitops-01.png)

## Deploy Grafana Dashboards
```bash
oc apply -k grafana-operator/overlays/instance/overlay
```

# 3 - Deploy Grafana Loki

```bash
cd custom-resources/kafka
oc apply -k loki/base
```
# 4 - Deploy Network Observability Flow Collector

```bash
cd custom-resources/kafka
oc apply -k netobserv/instance/overlays/default/
```

* Agent: can be EBPF (this case and the default one) or IPFIX (OVN-Kubernetes for example). EBPF is recommended and offers more performance.
* Sampling: value of flows sampled. By default is is set to 50 (1:50) for EBPF and 400 for IPFIX (1:400). This means that one flow of every 50 is sampled.
* Deployment Model: Direct model (no Kafka used)
* Status: the actual status of the Netobserv FlowCollector
* The FlowCollector resource includes configuration of the Loki client, which is used by the processor (flowlogs-pipeline) to connect and send data to Loki for storage:

# OpenShift Console Plugin
* Overview Metrics - Charts on this page show overall, aggregated metrics on the cluster network:
![OpenShift NetWork Traffic](images/gitops-01.png)

* Topology - The topology view represents traffic between elements as a graph:
![Topology](images/gitops-01.png)

* Flow table - The table view shows raw flows, ie. non aggregated, still with the same filtering options, and configurable columns.
![Flow Table](images/gitops-01.png)

* Network Traffic of some specific Pods
![Traffic Pods](images/gitops-01.png)