---
title: "Hello kubectl cost: monitoring Kubernetes spend from the command line!"
date: 2021-04-20T11:34:00-04:00
canonical_url: "http://blog.kubecost.com/blog/kubectl-cost-kubernetes-monitoring-cli/"
classes: wide
categories:
  - blog
tags:
  - cost monitoring
  - Kubecost
author: Michael Dresser
---

If you're terminal-loving engineers using Kubernetes like us, kubectl is your constant companion. That's why the Kubecost team built a new CLI for interacting with Kubernetes cost data. Today, we’re announcing [kubectl cost](https://github.com/kubecost/kubectl-cost), an open-source extension that fits directly into your workflow.

Here’s an example of it in action: 

![GIF of usage](/assets/images/kubectl-cost-usage-shortened.gif)

For teams running Kubernetes, gaining visibility into the cost of resources can be hard, especially in dynamic multi-tenant environments. [Kubecost](https://www.kubecost.com/) helps teams—developers, managers, executives, and everyone in-between—running Kubernetes understand their cluster spend precisely, all the way down to the pod level. One of our primary goals is to provide cost visibility into tools that teams are already using. 

Kubectl cost is a [kubectl plugin](https://kubernetes.io/docs/tasks/extend-kubectl/kubectl-plugins/), a CLI tool designed for application and infrastructure engineers who interact directly with Kubernetes on a regular basis. They would benefit from understanding the costs of their various deployments and other in-cluster resources. With reporting a few keystrokes away on the familiar interface of `kubectl`, the `cost` plugin gives engineers quick and easy access to cost and spend efficiency information. At Kubecost, we believe that by making cost metrics more accessible we can help our users build more cost-efficient software systems. Let’s check it out.

# Using `kubectl cost`

The basic structure of `kubectl cost` is built around various aggregations that map to Kubernetes concepts, e.g. namespace, label, deployment, statefulset, etc. It leverages Kubecost APIs which provide users with programmatic access to useful data about workloads and assets in your clusters. 

Let’s have a look at a few samples:

![Namespace aggregation example](/assets/images/kubectl-cost_namespace.png)

One of the simplest queries, showing a monthly cost projection for each namespace in your cluster based on the past day of activity. This accounts for all workloads and their resources in each label. 

![Label aggregation example](/assets/images/kubectl-cost_label.png)

Total cost, over the past day, broken down by the value of the `app` label. This accounts for labels applied at both the namespace and workload-level. 

![Deployment aggregation example](/assets/images/kubectl-cost_deployment.png)

Monthly rate projection broken down by deployment, including a more detailed look at CPU cost and CPU cost efficiency.

![Namespace historical](/assets/images/kubectl-cost_namespace_historical.png)

How much each namespace cost last month, including CPU cost and efficiency.

![Namespace historical all metrics](/assets/images/kubectl-cost_namespace_historical_all.png)

How much each namespace cost yesterday, with all resource-specific costs and efficiencies displayed. This highlights the granular detail at which Kubecost collects cost metrics. 

# Installation

The `kubectl cost` plugin runs in any cluster running Kubernetes version 1.08 or higher with a Kubecost installation. You can get Kubecost into your cluster in a matter of minutes by following [Kubecost installation instructions](https://docs.kubecost.com/install). 
Once that’s done, we can install kubectl cost—it’s also free and open source (Apache 2) and typically takes less than a minute to install.

### Krew
If you have [Krew](https://krew.sigs.k8s.io/), the kubectl plugin manager, already installed, getting kubectl cost is as simple as running:
```
kubectl krew install cost
```

### Linux and MacOS

```
os=$(uname | tr '[:upper:]' '[:lower:]') && \
arch=$(uname -m | tr '[:upper:]' '[:lower:]' | sed -e s/x86_64/amd64/) && \
curl -s -L https://github.com/kubecost/kubectl-cost/releases/latest/download/kubectl-cost-$os-$arch.tar.gz | tar xz -C /tmp && \
chmod +x /tmp/kubectl-cost && \
sudo mv /tmp/kubectl-cost /usr/local/bin/kubectl-cost
```
### Install from source
If you would prefer to build from source, you can check out the [README](https://github.com/kubecost/kubectl-cost#latest-release) of kubectl cost for detailed instructions.

# How it works
- By default, Kubecost integrates with cloud provider billing APIs with support for AWS/EKS, Azure/AKS, GCP/GKE, and on-prem clusters via custom pricing sheets.
- Kubecost can integrate with your cloud provider billing data directly to accurately reflect enterprise discounts, spot prices, reserved instances, savings plans, and more.
- Compute and memory costs are calculated using the max of resource usage and resource requests.
- Network costs are optional and are enabled via the [network-costs daemonset](https://github.com/kubecost/docs/blob/master/network-allocation.md). 
- Monthly rate projections are based on average run rate for each individual workload over the measured window. 

# Learning more
There’s tons more to discover, check out the [documentation](https://github.com/kubecost/kubectl-cost/blob/main/README.md) and `kubectl cost --help` to keep going. We’re also going to be adding more functionality in the coming weeks. So [join our Slack community](https://join.slack.com/t/kubecost/shared_invite/enQtNTA2MjQ1NDUyODE5LWFjYzIzNWE4MDkzMmUyZGU4NjkwMzMyMjIyM2E0NGNmYjExZjBiNjk1YzY5ZDI0ZTNhZDg4NjlkMGRkYzFlZTU) or reach out to team@kubecost.com if you have questions or additional features you’d like to see!
