---
title: "How to Install and manage Kubecost via Helm Chart using Lens IDE"
description: "Learn how you can use Lens IDE to easily install, update, and troubleshoot Kubecost on any Kubernetes cluster."
date: 2022-04-28T08:00:00-04:00
canonical_url: "https://blog.kubecost.com/blog/how-to-install-and-manage-kubecost-via-helm-using-lens"
classes: wide
categories:
  - blog
tags:
  - Kubernetes
  - Kubecost
  - cost monitoring
  - Lens
  - Helm
author: Andrew Dawson
---

Using the Lens IDE makes installing, updating, and troubleshooting your Kubecost Helm release extremely simple. Follow the guide below to set up Kubecost using Lens IDE.

![image alt text](/assets/images/lens-with-kubecost/kubecost-lens-1.png)

# Kubecost + Lens IDE.

When working with Kubecost and your Kubernetes cluster as a whole, visibility is key. Being able to quickly see how all your different objects are interacting with each other is key to being able to optimize your cluster. Although the command line is all-powerful, sometimes k8s developers want to interact with a simple graphical interface—that’s where [Lens, the Kubernetes Integrated Development Environment (IDE) by Mirantis](https://k8slens.dev/), comes in.

Kubecost users connect their clusters under management within Lens, allowing for simple multi-cluster administration. Each cluster ‘workspace’ has its own built-in terminal set to the corrpospending kubeconfig entry, making it quick and easy to use the command line + the correct kubeconfig settings for that cluster. This can be especially useful for orginizations using [Kubecost Enterprise with multiple federated clusters](https://guide.kubecost.com/hc/en-us/articles/4407601809175-Kubecost-Enterprise-Features).

## Install + Manage Kubecost Enterprise via Helm Chart using Lens IDE

One of the benefits of Kubecost is our easy to manage [Helm chart](https://guide.kubecost.com/hc/en-us/articles/4407601821207-Installing-KubecostUsing). Lens makes installing, updating, and troubleshooting your Kubecost Helm release extremely simple. 

## Simplify Kubecost port forwarding, logs, and pod shells

Using Lens, users can verify all Kubecost related pods are running and see any errors easily using the cluster dashboard and specifiying your Kubecost namespace. This is helpful when deploying Durable Storage or troubleshooting a custom integration or settings change. Lens also allows Kubecost users to get to the cost-model container logs and container shell with a few clicks.

## Port-Forward without the CLI Command

 Lens allows for simple and secure access to Kubecost services via port forwarding. For those who do not want to expose Kubecost via Ingress or Load Balancer, Lens makes accessing via Service Port Forwarding very easy. Team members with access to the cluster through Lens can access Kubecost securely through the 'Services' section. 

## Follow the guide below to set up Kubecost Helm release using Lens: 

### Step 0: Generate a kubeconfig entry for your cluster.

Prerequisite: You will need to have active kubeconfig entry for a kubernetes cluster. In this example, we use Google Kubernetes Engine, but most k8s clusters can be added with this same method.

Generate a config file on your local machine for your cluster. To do this for your GKE cluster, you can click “Connect” on the top of the console. Copy the command-line access command onto your clipboard.

Paste the command into your terminal on your local machine. You will need to have Google Cloud CLI installed on your machine and configured to your project.

### Step 1: Download the latest version of Lens IDE.

Download [Lens, the Kubernetes IDE by Mirantis](https://k8slens.dev/) and install in on your local machine.

### Step 2: Add your cluster to Lens.

Open Lens on your local machine and click on “Browse Clusters in Catalog.” You will see your cluster in the list, but it will be marked “disconnected”.

![Click 'Browse Clusters in Catalog'](/assets/images/lens-with-kubecost/kubecost-lens-2.png)

Click “Connect” on the cluster, and Lens will start the connection process.

![Click on 'Connect'](/assets/images/lens-with-kubecost/kubecost-lens-3.png)

Once connected, you’ll have a full graphical view of your K8s objects, as well as a built-in terminal connected to that cluster.

![Cluster View](/assets/images/lens-with-kubecost/kubecost-lens-4.png)

### Step 3: Give your cluster a friendly name and other optional settings.

Go to the top left corner and drop down the menu, then click “Settings”. Within the settings, you can change the cluster display name, upload an icon, and adjust other settings such as for the cluster.

![General Settings](/assets/images/lens-with-kubecost/kubecost-lens-5.png)

### Step 4: Prep your cluster for Kubecost installation

Now that the cluster is set up in Lens, open the in-product Terminal. Create the namespace for your new Kubecost installation with the command kubectl create namespace kubecost.

![Create 'kubecost' namespace](/assets/images/lens-with-kubecost/kubecost-lens-6.png)

One the namespace is created, add the Helm repo for Kubecost with the command helm repo add kubecost https://kubecost.github.io/cost-analyzer/

![Get the updated Kubecost repo from Helm](/assets/images/lens-with-kubecost/kubecost-lens-7.png)

### Step 5: Install the Kubecost Helm release using the Lens console. 

On the left side of the Lens menu, navigate to to “Helm”, then click “Charts”. Search for “cost” in the search bar. You will see the Helm Chart for the Kubecost cost-analyzer that was added in the previous step.

![Locate the Kubecost Helm chart](/assets/images/lens-with-kubecost/kubecost-lens-8.png)

Click the chart and the side information panel will pop up. You can pick the version of Kubecost you want to install, as well as view common [Kubecost Helm values](https://github.com/kubecost/cost-analyzer-helm-chart/blob/master/cost-analyzer/values.yaml)

![View Kubecost chart information](/assets/images/lens-with-kubecost/kubecost-lens-9.png)

After clicking Install, you are given the option to modify different options before deploying. Select the “Kubecost” namespace we created in Step 4, and give the release a friendly name like “kubecost”. The Helm values are shown in the terminal window and can be edited before deployment.

Click the “Install” button and your Helm Chart will install. 

![View Kubecost chart information](/assets/images/lens-with-kubecost/kubecost-lens-10.png)

### Step 6: Verify your Kubecost release is available and view objects

Within Lens, click on "Workloads". Select the Kubecost namespace to see all the Kubenetes objects that have beeen instaled via the Helm release. You should see all green. If you see any workloads that are unavailable, your cluster may not have enough resources to run Kubecost. 

![View Kubecost workloads in Lens](/assets/images/lens-with-kubecost/kubecost-lens-11.png)

### Step 7: Using the "Helm/Release" section of Lense to manage your Kubecost release.

Once Kubecost is available, you can click on “Helm/Releases” to see your release within Lens.

![View Helm releases](/assets/images/lens-with-kubecost/kubecost-lens-12.png)

The Helm Release section allows you to update the Kubecost version and Helm values easily. Advanced options can be configured through the values file, like bringing in [external non-k8s cloud costs from AWS, GCP and Azure accounts](https://guide.kubecost.com/hc/en-us/articles/4412369153687-Cloud-Integrations), [SSO setup](https://guide.kubecost.com/hc/en-us/articles/4407595985047-User-Management-SSO-SAML), and more.

![Helm release details](/assets/images/lens-with-kubecost/kubecost-lens-13.png)

Under Helm → Releases, click on the right side drop down menu and select Upgrade. This pop up screen allows you to add and edit Helm Values right within Lens, as well as upgrade your Kubecost version to the latest release by selecting it from the “Upgrade version” drop down.

![Upgrade to new Kubecost version via Helm release](/assets/images/lens-with-kubecost/kubecost-lens-14.png)

### Step 8: Access Kubecost using port forwarding through Lens

To access Kubecost, go to “Services” and fine the kubecost-cost-analyzer service. Scroll down, and find the “Connection/Ports” section. You can click "Forward" and set the port to 9090. If you have multiple clusters, they can't all use port 9090. In this case, you can use a randomized port. To do this, click on the link text for 'Port 9090' directly. 

![Select port 9090 via Services](/assets/images/lens-with-kubecost/kubecost-lens-15.png)
 
Kubecost will open on a randomized port - Copy the url from the URL bar and paste it into the “Add New Cluster” 

![Add new port to Kubecost](/assets/images/lens-with-kubecost/kubecost-lens-16.png)

You will now be able to access your cluster! Kubecost core version is free forever on one individual cluster per company, with 15 day metric retention. [Kubecost Enterprise](https://guide.kubecost.com/hc/en-us/articles/4407601809175-Kubecost-Enterprise-Features) provides federated views for multiple clusters, SSO, unlimited metrics, and dedicated support.

![Access Kubecost dashboard](/assets/images/lens-with-kubecost/kubecost-lens-16.png)

## We’re here to help!

[Join us on Slack](https://join.slack.com/t/kubecost/shared_invite/enQtNTA2MjQ1NDUyODE5LWFjYzIzNWE4MDkzMmUyZGU4NjkwMzMyMjIyM2E0NGNmYjExZjBiNjk1YzY5ZDI0ZTNhZDg4NjlkMGRkYzFlZTU) for any other help, and general Kubernetes and Cloud Cost optimization banter!






