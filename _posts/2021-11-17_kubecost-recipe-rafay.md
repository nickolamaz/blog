---
title: "Kubernetes cost visibility and analytics with Kubecost and Rafay"
description: "Rafay’s Kubecost recipe allows users to simplify and automate deployment of Kubecost across new and existing clusters, giving teams powerful visibility into Kubernetes spend."
date: 2021-11-17T8:00:00-04:00
canonical_url: "https://blog.kubecost.com/blog/kubecost-recipe-rafay"
classes: wide
categories:
  - blog
tags:
  - Monitoring
  - Kubernetes
  - Cost Savings
  - CICD
---

Kubernetes is a powerful container orchestration system that enables organizations to automate modern applications across public clouds, data centers, and the edge. While Kubernetes allows teams to quickly deploy and scale applications, it presents a challenge for IT departments in understanding the costs of their workloads. To solve this cost visibility challenge for their users, Rafay’s new Cost Management category features a recipe to automate deployment of Kubecost across an organization's clusters. Available through Rafay’s Kubernetes Operations Platform (KOP), this template simplifies the process of configuring Kubecost across Rafay clusters—making deep performance insights possible and allowing you to take advantage of optimization opportunities identified by Kubecost.

## What is Kubecost?

[Kubecost](https://www.kubecost.com/) started in early 2019 as an open-source tool providing comprehensive cost monitoring and optimization for teams running Kubernetes. With its core features, Kubecost gives organizations complete visibility into Kubernetes spend:

* Cost allocation: Kubecost allows you to break down allocated spend across all native Kubernetes concepts, so you can provide your teams with transparent, accurate cost data reconciled with your actual cloud bill.

* Unified cost monitoring: joining in-cluster costs like CPU and memory with out-of-cluster spend from cloud infrastructure services gives complete cost visibility across AWS, GCP, and Microsoft Azure.

* Optimization insights: Kubecost automatically generates recommendations you can use to save 30-50% or more on infrastructure spend (all without exposing private information—Kubecost is installed on prem with no data egress).

* Alerts and governance: with real-time alerting functionality and recurring reports, Kubecost empowers teams to take control of their Kubernetes-enabled infrastructure, stay within budgeted limits, and address monitoring interruptions immediately.

![Kubecost overview page](/assets/images/rafay-kubecost-overview.png)

## Rafay Kubernetes Operations Platform

Rafay’s KOP provides a holistic approach to managing modern infrastructure by dramatically simplifying the lifecycle management of Kubernetes clusters and modern applications located in data centers, public clouds or at the edge. With Rafay, enterprises can use any Kubernetes distribution and immediately gain centralized automation, security, visibility, and governance capabilities with features for:

* Multi-cluster management: Lifecycle management and blueprinting support for managed Kubernetes services, such as Amazon EKS and Azure AKS, for packaged offerings such as RedHat OpenShift, and for upstream Kubernetes deployments. 

* Gitops: Enables infrastructure orchestration and application deployment through multi-stage, git-triggered pipelines.

* Zero-trust access: Enables controlled, audited access for developers, SREs and automation systems to Kubernetes infrastructure.

* Kubernetes policy management: Enables policy management for clusters via the Open Policy Agent (OPA) framework for Kubernetes security and governance.

* Backup and restore: Enables disaster recovery and migration of the Kubernetes control plane and application data.

* Visibility and monitoring service: Enables development, operations and security/governance teams to visualize and monitor modern apps and underlying Kubernetes infrastructure through dedicated dashboards.

![Rafay overview](/assets/images/rafay-rafay.png)

## Helping organizations get control of their Kubernetes costs

Managing costs inside of Kubernetes clusters gets more complex at scale. Organizations typically start their Kubernetes adoption journey with test clusters, quickly moving to a more structured environment that includes QA, staging, and production clusters. Additionally, clusters scale across regions and grow as new workloads are added. 

By taking advantage of Rafay’s cluster blueprint feature, which is documented in the Rafay - [Kubecost recipe](https://docs.rafay.co/recipes/cost/kubecost/), organizations can seamlessly deploy Kubecost to each new cluster as the cluster gets created. This enables SRE and DevOps teams to understand their costs in every Kubernetes cluster, providing teams with the ability to optimize infrastructure and control costs. 

## Get started with Rafay and Kubecost

With a repeatable, automated process for deploying Kubecost into new and existing clusters, Rafay and Kubecost make it easier for teams working with Kubernetes to simplify and optimize their infrastructure—giving users complete visibility into Kubernetes spend. If you're already a Rafay user, you can start realizing the benefits of unified cost monitoring today with the [Kubecost recipe](https://docs.rafay.co/recipes/cost/kubecost/).

Kubecost can be deployed with Helm in any Kubernetes cluster in minutes! Visit our [install page](https://www.kubecost.com/install) to get started.
