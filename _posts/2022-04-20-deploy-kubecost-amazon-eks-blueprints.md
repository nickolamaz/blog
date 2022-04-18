---
title: "Easily deploy Kubecost on AWS using Amazon EKS Blueprints"
description: "Learn how to easily deploy Kubecost on AWS using Amazon EKS Blueprints in this step by step blog."
date: 2022-04-17T08:00:00-04:00
canonical_url: "https://blog.kubecost.com/blog/deploy-kubecost-amazon-eks-blueprints"
classes: wide
categories:
  - blog
tags:
  - Kubernetes
  - Kubecost
  - cost monitoring
---

If you've ever dabbled with Infrastructure as Code, or it's something you've been interested in doing, we think you're going to like this one... 🥁

![image alt text](/assets/images/deploy-kubecost-amazon-eks-blueprints/image_0.png)

Kubecost can now be deployed and configured on Amazon EKS using AWS [Cloud Development Kit (CDK)](https://aws.amazon.com/cdk/) as an EKS Blueprint!

## What are Amazon EKS Blueprints?

EKS Blueprints are a way to abstract cloud infrastructure complexity away from software developers. Blueprints allow developers to deploy containerized workloads using tools and languages that they are already familiar with. With the help of EKS Blueprints, teams can consolidate tools and best practices into a single central platform that can then be used across their organization.

A Blueprint is typically composed of multiple AWS or open source products and services, including services for running containers, CI/CD pipelines, capturing logs/metrics, and security enforcement. Blueprints can help package these tools into a cohesive whole and make them available to development teams as a service.

## How Kubecost helps

Given the sheer scale and complexity of Kubernetes environments, tracking cloud spend can quickly become problematic. For any organization running services on Kubernetes, having a way to continuously monitor and optimize costs is an important best practice to introduce and automate early on.

Kubecost automatically provides cost visibility, savings optimizations, and ongoing governance for EKS deployments, and presents a unified view of these costs along with those of all other Kubernetes infrastructure. With Kubecost, users reduce the operational burden of managing multiple cost views and manually tracking spend for each of their services.

The Kubecost EKS Blueprint AddOn allows teams to automatically provision and maintain Kubecost across multiple clusters, making it part of the internal development platform for the enterprise. The AddOn can be deployed and configured as part of your EKS Blueprint using AWS CDK (Cloud Development Kit), with just a few lines of TypeScript or JavaScript code!

## About the Kubecost EKS Blueprint AddOn

You can use the [EKS Blueprint Kubecost AddOn](https://github.com/kubecost/kubecost-ssp-addon/) to:

1. Install Kubecost, along with its dependencies Prometheus, Grafana, and kube-state-metrics in the kubecost namespace from the official Kubecost Helm chart.

2. Configure a specific Kubecost version.

3. Set custom values for the values.yaml file.

All using CDK and TypeScript or JavaScript.

## How to use the AddOn

### Create a CDK project

To get started, you’ll first need to install appropriate versions of AWS CLI, AWS CDK, and then bootstrap a CDK project. Follow [the EKS Blueprint Quick Start documentation](https://aws-quickstart.github.io/cdk-eks-blueprints/) to go through those steps.

Once you’ve bootstrapped the project, go ahead and install the eks-blueprints library, which will allow you to use all the EKS Blueprint magic.

```
$ npm install @aws-quickstart/eks-blueprints
```

### Install Kubecost EKS Blueprints AddOn

Install the Kubecost library in your project’s working directory:

```
$ npm install @kubecost/kubecost-eks-blueprints-addon
```

### Write some TypeScript code 👩‍💻

You'll notice that running the bootstrap command created some files and folders within your working directory. We'll create a blueprint with the Kubecost AddOn, and then apply it to the cluster.

Note that id is the cluster id. You have two options: either use an existing cluster ID in that region, which will install Kubecost on an existing cluster. Alternatively, give it a new id, which will provision a brand new cluster under the associated AWS account in that region.

Replace the contents of `bin/<your-main-file>.ts` (where your-main-file by default is the name of the root project directory) with the following:

```ts
import "source-map-support/register";
import * as cdk from "aws-cdk-lib";
import * as blueprints from "@aws-quickstart/eks-blueprints";
import { KubecostAddOn } from "@kubecost/kubecost-eks-blueprints-addon";

const app = new cdk.App();
const addOn = new KubecostAddOn();
const blueprint = blueprints.EksBlueprint.builder()
  .addOns(addOn)
  .build(app, "my-stack-name");
```

Deploy and apply the blueprint using the following command:

```
$ cdk deploy
```

 

Give it some time... and there we are! Once you’ve deployed Kubecost this way, you’ll be able to view the dashboards using kubectl port-forward command. 

```
$ kubectl port-forward --namespace kubecost deployment/cost-analyzer 9090
```

 

Once the Blueprint is set up, it can be deployed in the same configuration across multiple regions and accounts, making sure that all of your clusters are uniform and consistently running Kubecost. The recommended approach for day-two operations is Git-driven [pipelines](https://aws-quickstart.github.io/cdk-eks-blueprints/pipelines/).

## Try it yourself!

Ready to give Kubecost and EKS Blueprints a try? Checkout the full [Blueprint documentation](https://aws-quickstart.github.io/cdk-eks-blueprints/) and [Kubecost AddOn documentation](https://github.com/kubecost/kubecost-eks-blueprints-addon) to get started.
