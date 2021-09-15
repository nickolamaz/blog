---
title: "GreenSteam Reduces Its Maritime Customers’ Carbon Footprints—and Optimizes Its Infrastructure Budget with Kubecost"
description: "Using Kubecost, GreenSteam was able to achieve total cost visibility and allocate costs down to individual vessels for the first time."
date: 2021-09-15T8:00:00-04:00
canonical_url: "https://blog.kubecost.com/blog/greensteam-case-study"
classes: wide
categories:
  - blog
  - case study
tags:
  - case study
  - AWS
  - cost monitoring
---

[GreenSteam](https://www.greensteam.com/), a leading marine data intelligence company, reduces the fuel waste and carbon footprint of its maritime shipping customers by optimizing vessel performance. Leveraging the power of Amazon Elastic Kubernetes Service (EKS), GreenSteam combines myriad data sources with machine learning to accurately measure each component of a vessel’s fuel consumption. Their platform transforms otherwise time-consuming and unwieldy analytics into simple, clear, and accurate vessel performance metrics. But when it came time to measure its own Kubernetes costs (which represent a major component of a vessel’s IT spend), GreenSteam ran into challenges—without the ability to drill into costs and attribute them at a granular level, they couldn’t see the total infrastructure cost of running a vessel. Using [Kubecost](http://kubecost.com), GreenSteam was able to achieve total cost visibility, uniting in- and out-of-cluster spend and allocating these costs down to individual vessels, for the first time.

## GreenSteam: stewards in vessel optimization for fuel savings

Launched in 2007, GreenSteam applies cloud-based machine learning to vessels’ fuel consumption—traditionally a major source of cost inefficiency for many maritime shipping organizations. GreenSteam leverages its team’s unique expertise in both ML and naval architecture to help vessel owners and operators continually optimize their fuel resources and reduce greenhouse gas emissions. GreenSteam’s platform captures, analyzes, and predicts the data required for its customers to make more informed operational decisions. 

 

GreenSteam relies on advanced machine learning to deliver the data customers require for:

* Identifying fuel-saving opportunities across their fleets by accurately measuring and identifying every contributing factor, including those that are often overlooked by other models;

* Optimizing the timing of expensive dry-dock and cleaning schedules;

* Delivering predictive advice that helps laden and ballast vessels to maximize operational efficiency.

* Combining historical baseline performance models with real-time data from on-board sensors, data from vessel systems, and weather and sea-state information to maximize operational efficiencies;

* Providing advice on vessel speeds to minimize fuel wastage while still meeting voyage deadlines.

 

Over the past two years, GreenSteam has identified more than 46,000 metric tons of wasted fuel and discovered potential fuel savings of more than $25 million.

 

{% include figure image_path="/assets/images/greensteam.jpg" alt="GreenSteam employee" caption="Source: greensteam.com" %}

## Kubernetes for today’s captains: running infrastructure on AWS EKS

At any given time, GreenSteam is continually tracking data across several hundred vessels with a combination of low frequency (averaged every 24 hours) and high frequency (averaged every 5 minutes) data. This data is brought to shore and combined with other sources, such as weather information, to produce a single-format data output. To ensure the scalability of its data processing, GreenSteam runs the core of its infrastructure on Amazon Elastic Kubernetes Service (EKS)—a particularly fitting choice, considering Kubernetes’ seafaring roots (*Kubernetes* is a Greek word that translates to "ship’s captain" or “helmsman”).

 

"We can scale up to more than 200 nodes on AWS; our main infrastructure is Kubernetes combined with data storage on S3," says John Boers, Team Lead and Senior Software Engineer at GreenSteam. “When the pipeline is triggered, the system spins up more nodes, assigns ports, and we process the data for each vessel.”

As they scaled their infrastructure, GreenSteam realized it needed a complete cost picture—drilling down to the individual pod level—to identify spend by workload and allocate costs to the vessels responsible for those costs. 

## A cleared horizon: Kubecost offers much-needed visibility into Kubernetes spending

GreenSteam began research into tools that could provide sufficient Kubernetes cost visibility and management. Although other cloud cost management tools offer limited visibility into Kubernetes, GreenSteam chose to trust Kubecost—the only cost management platform purpose-built for visibility into Kubernetes.

 

Kubecost was able to give GreenSteam the granular insights it needed to accurately measure how much each workflow was costing the company. This meant—for the first time—the company could see how much each individual vessel cost them from a Kubernetes environment perspective.

"Kubecost enables us to see our overall spend, but it also helps us drill down into our IT costs for supporting each vessel," explains Boers. “That means we are now able to see costs of our processes and workloads, and the detailed costs associated with a namespace at every level. Kubecost gives us the knowledge of how much each workflow is costing us, so we know how much money is spent on each vessel. It’s important information that we can use to make business decisions based on.”

 

GreenSteam now leverages Kubecost for:

* **Cost allocation:** Kubecost enables GreenSteam to easily see allocated spend across all native Kubernetes concepts. GreenSteam can provide its teams with transparent, accurate cost data reconciled with the actual cloud bill from AWS.

* **Unified cost monitoring:** GreenSteam has a unified view of its spend by joining real-time costs from Kubernetes clusters (CPU, memory, storage, and network) with outside costs (such as S3 buckets).

## Navigating ahead with Kubecost’s precise and actionable insight into Kubernetes and cloud costs

Nearing 15 years in business, GreenSteam is the clear leader in its industry. However, it knows that to retain its reputation and customers, the company must continue to advance its data-intensive platform. Keeping up with this demand for innovation—while continuing to meet customers’ expectations for their platform’s availability and performance—needs to be balanced with cost optimization, which is why Greensteam trusts Kubecost to keep cloud expenses visible.

 

"To keep us as the leader in our space, our executive team needs to have actionable insights into the technology cost of our customers," concludes Boers. “How much did it cost to host a vessel on AWS EKS? What does it cost per day? What should we charge for a monthly customer subscription? What would it cost to add new services?  These numbers were simply not there before Kubecost. I do believe that Kubecost is a very good tool that gives very good insight.”

## Conclusion

With Kubecost’s cost allocation and unified cost monitoring functionalities, GreenSteam can accurately track and attribute real-time Kubernetes costs to its individual vessels—and deliver powerful fuel savings and vessel optimization to its customers. Ready to set sail for greater visibility into your Kubernetes spend? Installing open source Kubecost for free takes five minutes and starts [here](https://www.kubecost.com/install.html).
