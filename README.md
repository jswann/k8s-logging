# Docker EE Logging Infrastructure

The following files will configure and deploy a container logging strategy for a Kubernetes runtime, specifically Docker Enterprise Edition Clusters.

## Architecture

The logging architecture leverages a modified version of the ELK Stack. This stack consists of the Elastic Search and Kibina utilities but instead of LogStash uses [Fluentd](https://docs.fluentd.org/) and [Fluent-Bit](https://docs.fluentbit.io/manual/) for the log collection and aggregation functions

## Prerequisites

* Enable `journald` engine [log driver](https://docs.docker.com/config/containers/logging/configure/)
* Enable presentient storage for Elastic Search

## Installation

1. Clone the repository:

```bash 
git clone https://github.com/jswann/k8s-logging.git
```

2. Configure and/or verify Storage Class

2. Configure ingress url in `kibana.yaml` file

2. Create `logging` namespace
```bash
kubectl create namespace logging
```

2. Apply Kubernetes files

```bash
kubectl apply -f .
```

2. Access `Kibana` by using the URL configured in the ingress portion of the `kibana.yaml` file

## Indexes

* _kube_sys_sysd_ - This index is a collection of all the Kubernetes system containers. Containers which start with names matching `k8s_.*_kube-system_.* k8s_.*_kube-public_.* k8s_.*_tc-system_.*`. This log also contains events and actions captured from the Kubernetes API

* _kube_user_sysd_ - This index contains user or non-system defined kubernete containers.

* _ucp_sys_sysd_ - This index contains the UCP Manager and worker container logs.

* _sys_sysd_ - This index contains all `journald` logs for all nodes

## References

* [Configure Log Drivers](https://docs.docker.com/config/containers/logging/configure/)
* [Docker Logging Design and Best Practices](https://success.docker.com/article/logging-best-practices)
* [Fluentd](https://docs.fluentd.org/)
* [Fluent Bit](https://docs.fluentbit.io/manual/)
