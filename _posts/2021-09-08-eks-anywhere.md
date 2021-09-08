---
title: "Use Kubecost to monitor EKS-Anywhere costs"
description: "Kubecost is an EKS-Anywhere Launch Partner"
date: 2021-09-08T8:00:00-04:00
canonical_url: "https://blog.kubecost.com/blog/eks-anywhere"
classes: wide
categories:
  - blog
tags:
  - Kubernetes
  - AWS
---

We are proud to announce that Kubecost is an EKS Anywhere Launch Partner. AWS EKS customers can now use Kubecost to achieve unified cost monitoring across their EKS and EKS-A environments.

## What is EKS-Anywhere?

Amazon EKS Anywhere (EKS-A) is a new deployment option for Amazon EKS that enables users to create and operate Kubernetes clusters on-premises, including on their own virtual machines (VMs). As more teams adopt  Kubernetes, their implementation often includes  hybrid  infrastructure environments, such as a combination of multi-cloud, on premise, and air-gapped. For these teams, EKS-A can be a powerful new service to extend the benefits of Amazon EKS to environments outside the AWS public cloud. You can learn more about the EKS-A launch [here](https://aws.amazon.com/blogs/aws/amazon-eks-anywhere-now-generally-available-to-create-and-manage-kubernetes-clusters-on-premises/).

## The challenge of blended Kubernetes environments

As Kubernetes environments increase in their complexity, so too do the challenges of measuring infrastructure spend. Even teams running Kubernetes in a single environment struggle to understand where their spend is going, i.e., which team, project, or application is spending how much on its resources. This problem is even greater when customers have to simultaneously track and aggregate costs for a multitude of Kubernetes clusters that span on-prem as well as multiple public clouds. As a result, engineering and infrastructure teams all too often end up with a nasty surprise in the form of a big bill at the end of the month. 

Kubernetes is a powerful tool for increasing portability across public cloud and hybrid environments. Using Kubernetes, teams can build applications and deployment specs once, and repeatably deploy almost anywhere they have Kubernetes running. Recent industry surveys [1, 2] confirm the strong link between the use of multi-environment infrastructure and maturing stages of Kubernetes adoption. 

## How does Kubecost help?

Kubecost automatically provides cost visibility, savings optimizations, and ongoing governance for EKS-A deployments out of the box, and presents a unified view of these costs along with those of all other Kubernetes infrastructure. With Kubecost, users reduce the operational burden of managing multiple cost views and manually tracking spend for each of their deployments. The majority of Kubecost’s users are able to reduce Kubernetes costs by 30-50%**,** some by even more than 50%. Now that Kubecost supports EKS-A, teams can extend the same benefits of Kubecost to their EKS-A workloads.

## Implementing Kubecost in EKS-A environments

Kubecost is a free and open-source tool designed to monitor your Kubernetes costs. Kubecost supports EKS-Anywhere environments—[contact our team](mailto:team@kubecost.com) to learn more. Any data collected by Kubecost never leaves the cluster, which makes it particularly well-suited for  security-conscious teams.

**To get started, just install Kubecost with Helm (takes ~2 minutes):**

```
helm repo add kubecost https://kubecost.github.io/cost-analyzer/
helm upgrade -i --create-namespace kubecost kubecost/cost-analyzer --namespace kubecost --set kubecostToken="eks-a"
```

Kubecost is available for download as a Helm chart at this link that contains further instructions: [https://www.kubecost.com/install.html](https://www.kubecost.com/install.html).

Optionally, you can connect Kubecost to your [AWS Cost and Usage report](https://guide.kubecost.com/hc/en-us/articles/4407595928087-AWS-Cloud-Integration). This will allow your cost reporting to reflect enterprise discounts, reserved instance commitments, spot node discounts, and other pricing that is unique to your account.

Kubecost will work out of the box across EKS and EKS-A environments. However, because EKS-A runs on your own on-premises infrastructure, the price you pay for infrastructure will likely differ from your cloud environments in EKS—a difference that you can measure using Kubecost. For higher accuracy, you can [apply custom pricing](https://blog.kubecost.com/blog/kubernetes-cost-monitoring/#entering-custom-pricing-values) for your on-premise workloads. 

**Final thoughts**

Amazon EKS Anywhere extends the power of Amazon EKS to environments outside of the AWS public cloud infrastructure. Kubecost works across Amazon EKS-Anywhere, EKS, and anywhere else Kubernetes is running, to provide users with truly unified cost monitoring. Within minutes, teams can achieve cost visibility, optimization opportunities, and ongoing governance by deploying Kubecost on EKS-A workloads. 

[1] [https://www.sumologic.com/blog/kubernetes-adoption/](https://www.sumologic.com/blog/kubernetes-adoption/) 

[2] [https://www.f5.com/company/blog/Kubernetes-is-winning-the-multi-cloud-war](https://www.f5.com/company/blog/Kubernetes-is-winning-the-multi-cloud-war) 
