---
title: "Optimizing Kubernetes applications with Kubecost and Spinnaker"
description: "Using Kubecost and Spinnaker, teams can achieve real-time cost visibility—and automatically apply insights to continuously reduce Kubernetes costs as they deploy software releases."
date: 2021-10-07T8:00:00-04:00
canonical_url: "https://blog.kubecost.com/blog/spinnaker-kubecost-integration"
classes: wide
categories:
  - blog
tags:
  - Monitoring
  - Kubernetes
  - Cost Savings
  - CICD
author: Alex Thilen
---

Identifying under- and over-provisioned resources is an important first step in reducing wasteful Kubernetes spend, but without a programmatic means of applying recommendations, engineers could spend valuable time making frequent manual adjustments. Kubecost has worked with Armory (creators of enterprise-grade software delivery platforms with Spinnaker at their core) to create an integration that solves this challenge. Using Kubecost and Spinnaker, teams can achieve real-time cost visibility—and automatically apply insights to continuously reduce Kubernetes costs as they deploy software releases.


## Identifying inefficiencies in your cluster

Kubecost automatically allocates your cluster’s costs across native Kubernetes concepts based on their resource usage. Understanding cost by higher-level concepts such as namespace or label provides transparency around application costs and visibility into cost drivers. With accurate cost reporting from Kubecost, you can implement a chargeback program to bill spend back to your business units. Teams can identify resource inefficiencies within their Kubernetes infrastructure by using the Kubecost Insights API—for example, to identify that a particular namespace is inefficient because it has overprovisioned CPU. If a namespace has requested 100 millicpu, but is only using 6 millicpu, Kubecost will flag this as an opportunity for optimization, and recommend a reduced CPU capacity. 

You could take these recommendations and manually apply them. However, as your software and configurations change, or increased demand drives additional load, you would need to continually update your infrastructure using the latest optimization metrics from Kubecost—a manual process that could get quite tedious. 

## Continuous cost efficiency with Kubecost and Spinnaker

For a more scalable approach, you can automate the application of Kubecost recommendations with a Spinnaker pipeline. 

Spinnaker is a continuous delivery tool originally developed and open sourced by Netflix and Google. Teams using Spinnaker can automate software deployment to any major cloud provider, while leveraging industry best practices. For example, using a Spinnaker pipeline, teams can automatically validate their software and configuration against various criteria before deploying to production. This enables teams to streamline their development processes and reduces the risk of unverified infrastructure reaching deployment, which can impact end-users. Today, hundreds of teams are using Spinnaker across millions of their production deployments.

By factoring in Kubecost metrics as part of deployment decisions, Spinnaker can automatically leverage Kubecost’s insights to reduce overprovisioned Kubernetes infrastructure. Integrating Kubecost and Spinnaker, teams can ensure continuous cost efficiency at scale. 

![Visual representation of continuous cost optimization with Kubecost and Spinnaker](/assets/images/spinnaker-kubecost-integration/flowchart.png)

The diagram above shows a high-level overview of the interaction between Kubecost, Spinnaker, and the Kubernetes control plane.

The flywheel begins with the Kubecost insights API producing cost efficiency metrics. As Spinnaker deploys your application to its pipeline, it uses the resource inefficiencies identified by Kubecost to dynamically adjust the resource requests provided to the Kubernetes scheduler. Spinnaker automatically repeats this process for deployments, as Kubecost continues to collect new metrics every minute.

## Deploying the integration

To integrate Kubecost and Spinnaker, we create a custom webhook that calls the Kubecost API for recommendations and automatically deploys those recommendations to a given namespace.

To set up the Kubecost and Spinnaker integration, follow the below installation steps:

* If you don’t already have it, install Spinnaker

* [Install Kubecost in minutes](https://www.kubecost.com/install#show-instructions)

* Add the Kubecost custom webhook stage

    * [General info on custom webhooks](https://spinnaker.io/guides/operator/custom-webhook-stages/#creating-a-custom-webhook-stage)

    * [Kubecost custom webhook](https://github.com/kubecost/docs/blob/master/spinnaker-custom-webhook.md)

    * Use the new Kubecost stage in a pipeline

![Screenshot of Spinnaker UI with the Kubecost extension](/assets/images/spinnaker-kubecost-integration/spinnaker-ui.png)

* Results for calculated target requests will be available in:

    * CPU: : `$(new String)(#stage[<Your-Custom-Stage>]["context"][“webhook”][“body”][“controllers”][0][containers][<your-container-name>][“target”][“cpuCores”]`

    * RAM: `$(new String)(#stage[<Your-Custom-Stage>]["context"][“webhook”][“body”][“controllers”][0][containers][<your-container-name>][“target”][“ramBytes”]`

* Give it a go, and let us know what you think! Kubecost’s support is here to take questions and feedback in [Slack](https://join.slack.com/t/kubecost/shared_invite/zt-6gkdgzdf-rMI1qAky4t6GkDMiIjpEzw) and [email](mailto:support@kubecost.com).

For more information and to view live demos of this integration, go here:

* [Video: Demo of Kubecost + Spinnaker integration in action](https://www.youtube.com/watch?v=kU02PWyx9Go) 

* [Video: Spinnaker Workshop: Cost Optimization with Kubecost’s founders](https://www.youtube.com/watch?v=OZ_V42nWans) 

## Conclusion

Kubecost’s goal is to bring cost visibility to teams in collaboration with tools they already use (like Spinnaker), so [let us know](mailto:team@kubecost.com) if you have ideas for future integrations—and look out for more joint launches like this from the Kubecost team in the future!
 

If you are interested in a managed, enterprise-grade version of Spinnaker, our friends at [Armory.io](https://www.armory.io/) bring the power of Spinnaker to customers with additional feature extensions and world-class support.

 
