---
title: "Rancher vs Kubernetes: It's not either or"
description: "Learn how Rancher and Kubernetes complement each other with Kubernetes providing container orchestration in a cluster of nodes and Rancher streamlining the management of multiple Kubernetes clusters."
date: 2022-01-20T08:00:00-04:00
canonical_url: "https://blog.kubecost.com/blog/rancher-vs-kubernetes"
classes: wide
categories:
  - blog
tags:
  - Kubernetes
  - Cost Savings
  - Rancher
---

Kubernetes (K8s) and Rancher are both open source projects focused on container management with enormous communities of contributors and users. 

[Kubernetes](https://kubernetes.io/) is the leader in container orchestration. It offers teams the flexibility to efficiently run containerized workloads across multiple public cloud providers and hybrid cloud environments. Kubernetes offers advanced scheduling and scaling capabilities to ensure application performance and high availability. However, its functionality focuses on managing resources within a single cluster. 

[Rancher](https://rancher.com/products/rancher), on the other hand, is a platform designed to manage multiple Kubernetes clusters. It eases Kubernetes cluster management in large environments in several ways. For example, Rancher simplifies operations such as cluster provisioning, centralized security management, and monitoring workloads using popular tools such as [Promet](https://prometheus.io/)[heus](https://prometheus.io/). Additionally, Rancher has an extensive application catalog of [Helm charts](https://rancher.com/docs/rancher/v2.5/en/helm-charts/) for various applications such as Kubecost, Prometheus, Grafana, and MySQL.

This article takes a close look at these two technologies and explains how they are different and complementary.

{% include figure image_path="/assets/images/rancher-vs-kubernetes/image_0.png" alt="Rancher as a Kubernetes platform" caption="Three Kubernetes clusters, each managing containerized workloads, with Rancher managing the Kubernetes clusters." %}


## Kubernetes vs Rancher: Is it a question of either-or?

Rancher and Kubernetes are complementary. 

Rancher becomes helpful to DevOps teams once they operate multiple Kubernetes clusters, which is a common practice. For example, almost all organizations have production and staging workloads in separate Kubernetes clusters. Additionally, many teams have more than one production Kubernetes cluster distributed across different geographical regions to ensure availability during regional outages. As Kubernetes adoption grows across an enterprise, cluster counts tend to increase—reflecting the need for individual business units, teams, or projects within the company to run their own containerized workloads.

Using multiple clusters leads to what’s often referred to as "Day-2" operational challenges. The diagram presented below separates standard operational tasks into Day-0, Day-1, Day-2 tasks. Day-2 operations include deploying new applications, monitoring application performance, alerting on problems, ensuring security, and smoothly running Continuous Integration and Continuous Delivery ([CI/CD](https://en.wikipedia.org/wiki/CI/CD)) processes to release code into production.

{% include figure image_path="/assets/images/rancher-vs-kubernetes/image_1.png" alt="Project operations lifecycle" caption="Day 0, Day 1, Day 2, and \"end\" of project operations. [Source](https://dzone.com/articles/defining-day-2-operations)." %}


In summary, Rancher is a Kubernetes cluster management software that provides a global view of multiple Kubernetes clusters. It helps automate and scale tasks across multiple Kubernetes clusters, such as deploying application stacks, ensuring the consistent use of the same version of Kubernetes software, centrally auditing security policies, and optimizing resources with a consistent approach across clusters.

## Rancher and Kubernetes: feature overview

Now that we have covered the basics, let’s review the specific features of Rancher and Kubernetes at a high level. 

### Important Kubernetes Features

The following table summarizes some of the key benefits of using Kubernetes:

<table>
  <tr>
    <td>Cloud provider-agnostic</td>
    <td>Kubernetes based platform is easily migratable across cloud providers</td>
  </tr>
  <tr>
    <td>Enables easy scaling</td>
    <td>Containerized applications are comparatively easier to scale as compared to traditional applications hosted in virtual machines (VM)</td>
  </tr>
  <tr>
    <td>Resource usage optimization</td>
    <td>Configuration parameters make it relatively easy to control cluster density and autoscaling </td>
  </tr>
  <tr>
    <td>Self-healing</td>
    <td>In case of a node failure, pods are automatically rescheduled to other nodes</td>
  </tr>
  <tr>
    <td>Environment consistency</td>
    <td>Eliminates the classic problem of "It works on my machine"</td>
  </tr>
</table>


#### Cloud provider-agnostic

While it is possible to run Kubernetes clusters on-premises, many organizations use the hosted Kubernetes platforms such as Google Cloud’s GKE, Amazon’s EKS, or the AKS service from Microsoft Azure to reduce costs and operational complexity. Because Kubernetes is open source and platform agnostic, it’s easy to migrate between cloud providers because the workloads are containerized, and the core functionality of Kubernetes is similar across public clouds. 

#### Enables easy application scaling

The ability to scale applications is one of the most significant advantages of using containers. Kubernetes automates the resource and service scaling processes with the cluster autoscaler and pod autoscalers, respectively. Refer to this [guide](https://www.kubecost.com/kubernetes-autoscaling/) for an in-depth tutorial on this topic.

The autoscaling functionality means cluster administrators and application developers can respond dynamically to traffic spikes by scaling the application horizontally (by replicating or removing pods) or vertically (by increasing or decreasing a pod’s computing resources). During low traffic periods,  both the application and the cluster can automatically scale down to reduce costs. 

#### Resource usage optimization 

Kubernetes provides the ability to efficiently assign pods to cluster nodes. Administrators can schedule pods with an affinity towards a node’s location, hardware performance, or even anti-affinity towards other pods already hosted on the same node.

By using these advanced scheduling techniques, Kubernetes can make hosting platform utilization more efficient and cost-effective. However, optimal cluster management requires more than just efficient scheduling. Later in this article, we will introduce Kubecost, a free tool designed to augment your Kubernetes cost reporting and management.

#### Self-healing

Kubernetes is designed to be highly resilient to pod and node failures. It also supports geo-distribution by scheduling pods on virtual machines in different public cloud availability zones (AZs) or physical data centers. 

For example, suppose a cloud provider experiences an outage in one of its availability zones, or a server rack fails in a data center. In that scenario, Kubernetes will automatically move pods scheduled for those nodes to different nodes that are still online. These self-healing features make the overall platform immune to many common disaster scenarios.

#### Environment consistency

"But it works on my machine!“ is often a point of contention between developers and SREs. With the advent of containers, environmental issues were reduced but not eliminated. Kubernetes helps in this area by ensuring that the environments are consistent during different stages of the application deployment: Development, staging, pre-production, and production. It also ensures consistency across cloud providers and servers located on-premises. 

Providers of continuous delivery tools leverage this functionality by adding a new feature to provision a [preview environment](https://jenkins-x.io/docs/build-test-preview/preview/) as part of the build process to test pull requests and branch builds before being deployed into a production environment. This helps make software development and delivery processes more robust.

![It works on my machine](/assets/images/rancher-vs-kubernetes/image_2.png)

The typical answer to environmental inconsistency is: "But it works on my machine." 

### Important Rancher features

Now that we understand the features and benefits of Kubernetes, let’s take a close look at the key features of Rancher. 

<table>
  <tr>
    <td>Cluster provisioning and import</td>
    <td>Rancher lets you create new clusters or add existing ones to it</td>
  </tr>
  <tr>
    <td>The concept of projects</td>
    <td>Rancher introduces the concept of projects for better grouping of namespaces</td>
  </tr>
  <tr>
    <td>Extended RBAC control</td>
    <td>User permissions can be configured per project across clusters</td>
  </tr>
  <tr>
    <td>Easy workload deployment</td>
    <td>Users can use the Rancher UI to deploy their workloads without updating a YAML file</td>
  </tr>
  <tr>
    <td>Monitoring and alerting</td>
    <td>Allows users to create notifications and push cluster logs to different backends</td>
  </tr>
  <tr>
    <td>Extensive application catalog</td>
    <td>Similar to the app store on your smartphone, but for Kubernetes </td>
  </tr>
</table>


#### Cluster provisioning and import

Rancher allows you to provision Kubernetes clusters on your favorite cloud provider using a single console. With Rancher, you don’t need to switch between GCP, AWS, or Azure consoles. 

If you have existing clusters and want to begin using Rancher to manage them, Rancher offers an option called "importing a cluster" intended for that scenario. Importing a cluster deploys agents on existing cluster nodes that help Rancher take over their management.

Furthermore, Rancher also has a provisioner called Rancher Kubernetes Engine (RKE). With RKE you can provision your desired version of upstream Kubernetes on your own on-premises servers or a cloud provider of your choice. 

#### The concept of projects

In the real world, applications are complex and span across namespaces. Namespaces are groups of cluster resources assigned usually to separate teams that need independent administrative control. Rancher provides a construct above traditional Kubernetes namespaces called "projects." Projects group namespaces together to provide a single point of control. 

Cluster administrators can apply RBAC (role-based access control) policies on projects that trickle down to namespaces. This eliminates the need for managing users within every namespace.  Rancher also reports on the resource usage of a particular project and providers other helpful operational metrics related to this use case. 

#### Extended RBAC control

Most teams run more than one Kubernetes cluster in production. This type of workload distribution means a single application can span multiple clusters, each possibly hosted on different public and private clouds. 

The Rancher concept of a project also helps in this case. Rancher extends project-level RBAC controls across Kubernetes clusters. A single user can be defined to have the same—or different—permissions across several Kubernetes clusters without needing different authentication keys to switch between clusters.

#### Easy workload deployment

You can use the Rancher user interface (UI) to deploy workloads on your clusters without creating complex deployment manifests. All of the options that you would configure using a YAML template are available in the UI. With just a few clicks, you can have an application up and running. 

#### Monitoring and alerting

Rancher can help you set up easy monitoring, alerting, and logging for your cluster. Monitoring and alerting is built on top of popular and proven tools such as Prometheus and Alertmanager. This functionality offers dashboards with RBAC control so that you can easily add members to them. Rancher also allows you to ship cluster logs to different logging providers, including third-party commercial enterprise tools such as Splunk or Elastic. 

#### Extensive application catalog

Rancher has an extensive catalog that simplifies the deployment of popular applications on your cluster using [Helm charts](https://helm.sh/). This concept is similar to a smartphone’s app store but for Kubernetes applications. 

It can be tedious to deploy complex applications on Kubernetes using traditional methods like manually updating manifest files. Rancher makes it trivial to deploy applications across multiple clusters. You can get up and running with applications like Kafka or JFrog with the click of a button. 

Kubernetes and Rancher provide all of the functionality required to orchestrate containers and do it efficiently across multiple Kubernetes clusters; however, they don’t address the growing cost management challenge inherent in such large environments. Fortunately, Rancher works seamlessly with Kubecost to offer an automated solution to the multi-cluster cost allocation challenge. 

## Cost management for Kubernetes 

You can deploy Kubecost with a few clicks from the Rancher application catalog of Helm charts. Kubecost then measures resource usage (CPU, memory, GPU, network, and disk) and calculates the costs by extracting the necessary information from the billing logs of cloud providers, user-defined custom pricing (for user-owned compute), or from pricing estimates where other data is not available. Users can then allocate the cluster costs by namespace or label, among other options. Most importantly, Kubecost supports a feature that makes it easy to align cost allocation with how Rancher organizes cluster resources. If you set  **field.cattle.io/projectId **in the Product Label field under "settings," Kubecost will attribute costs by Rancher Projects. 

{% include figure image_path="/assets/images/rancher-vs-kubernetes/image_3.png" alt="Set the Project label in the Kubecost UI" caption="The Kubecost general settings page" %}

This is a powerful feature because Kubecost can help you allocate costs for a Rancher Project when you group applications across different namespaces under a single Rancher Project. Furthermore, with the help of pod labels, Kubecost can break down costs for each application component inside the Project. Kubecost also accounts for costs of non-cluster (external) resources such as a public cloud database services (e.g., [AWS RDS](https://aws.amazon.com/rds/)) used by Kubernetes resources. Finally, it helps measure the health and efficiency of a Kubernetes cluster. Kubecost is free forever for one cluster, so [try it for yourself](http://demo.kubecost.io/)!

## Summary

The rapid adoption of Kubernetes leaves many teams with the cumbersome reality of managing too many clusters. Rancher is solving this pain point by simplifying and automating Kubernetes cluster management. With the addition of Kubecost, teams can allocate costs across clusters by aligning with the core concept of a Rancher Project, and using labels to further refine their cost visibility. 
