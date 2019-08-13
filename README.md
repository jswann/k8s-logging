# Docker EE Logging Infrastructure

The following files will configure and deploy a container logging strategy for a Kubernetes runtime, specifically Docker Enterprise Edition Clusters.

## Architecture

The logging architecture leverages a modified version of the ELK Stack. This stack consists of the Elastic Search and Kibina utilities but instead of LogStash uses [Fluentd](https://docs.fluentd.org/) and [Fluent-Bit](https://docs.fluentbit.io/manual/) for the log collection and aggregation functions

## Prerequisites

* Enable `journald` engine [log driver](https://docs.docker.com/config/containers/logging/configure/)
* Enable presentient storage for Elastic Search

## Installation

1. Clone the repository:

`$ git clone https://github.com/jswann/k8s-logging.git`

## References

* [Configure Log Drivers](https://docs.docker.com/config/containers/logging/configure/)
* [Docker Logging Design and Best Practices](https://success.docker.com/article/logging-best-practices)
* [Fluentd](https://docs.fluentd.org/)
* [Fluent Bit](https://docs.fluentbit.io/manual/)
