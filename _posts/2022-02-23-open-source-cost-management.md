---
title: "Kubecost: bringing open source to cloud cost management"
description: "The future of cost monitoring is open source—learn why the founders of Kubecost left Google to build cloud-agnostic tools every Kubernetes developer team can afford."
date: 2022-02-23T08:00:00-04:00
canonical_url: "https://blog.kubecost.com/blog/open-source-cost-management"
classes: wide
categories:
  - blog
tags:
  - Kubernetes
  - Kubecost
  - cost monitoring
author: Webb Brown
---

*Last week we [announced](https://blog.kubecost.com/blog/series-a-funding-announcement/) our $25 million fundraise, so I wanted to take this opportunity to share our origin story, and look ahead to where we are going as a result of this milestone.*

Biking across Google’s Mountain View campus, I can still remember how excited I was to hear more about this new project my former teammate was working on: it was called Kubernetes. The project had launched in production the year before, and while I’d read enough to have a sense of its goals, I still hadn’t heard the full story until lunch that day. 

Over lunch, I heard all about how the incredible team (a lot of them having worked on Borg) had the grand vision for bringing container orchestration at global scale to any cloud provider or data center. They were planning to do this with an entirely open source framework and a neutral governance model that placed power, control, and flexibility directly in the hands of the community. At the time, I didn’t realize how much lunch that day would shape the next decade of my life—ultimately inspiring me to leave Google, start a company, and raise $25 million with the goal of helping millions of developers one day. 

![google bike](/assets/images/open-source-cost-management/image_0.jpg)

# Cost, performance, and health: the vision behind Kubecost

Soon after this experience, my soon-to-be cofounder Ajay Tripathy and I began noticing how early adopters of Kubernetes were struggling with the same challenges we were focused on at Google: balancing cost, performance, and health. The decentralized and dynamic nature of container orchestration was making it harder for Kubernetes users to understand and monitor infrastructure costs alongside performance and reliability metrics—and these same complexities made it significantly harder to optimize across these three areas. Specifically, finding the right amount and type of infrastructure that doesn’t cause major overspending (due to over-provisioning), but also doesn’t create real performance or reliability risks for applications (due to under-provisioning).

Since engineers can’t resist challenging optimization problems, we started brainstorming ways to help teams adopting Kubernetes navigate these complexities. We had used a number of existing third-party solutions, but found those to be focused on managing VM-based spend whereas the challenges Kubernetes users were facing called for new solutions developed specifically for their needs. 

Our vision to build something different became clear as we explored different ways to tackle this problem. Our experience at Google taught us that by developing solutions specifically for *Kubernetes users* (i.e. the engineers working directly with infrastructure and containerized applications), we could empower engineers themselves to directly optimize compute spend—giving them visibility into usage, performance risk, and costs, to ultimately improve their organization’s efficiency.

From the beginning, we knew we wanted to align with the founding principles of Kubernetes: we had to start with an open source project that would empower developers with data and give users ownership over the product’s evolution. This belief led us to build the first open source Kubecost over the course of a weekend. We weren’t sure where it would take us, but we wanted to validate our understanding of the problem and, frankly, needed a way to monitor our own Kubernetes clusters. After what happened next, we quickly realized we needed to start a company to have maximum impact with the project.

# Launching Kubecost

Within days of our initial launch in 2019, 100+ teams were using Kubecost to gain visibility into their cost and cost efficiency. Thrilled to have an early community of engineers focused on Kubernetes infrastructure optimization, we started talking to users—and quickly realized that even Kubernetes users that were early in their adoption journey were struggling with these challenges in a meaningful way. Using their insights and feedback, we initially prioritized providing users with great visibility, a choice that was rooted in our belief that you can’t optimize what you can’t measure. 

We built our product experience based on 4 strongly held beliefs: 

1. Every team should have free access to our core software, no matter their budget.
2. Developers should be able to install and experience all Kubecost features in minutes without contacting sales.
3. Our software should be open, transparent, and emphasize interoperability—users should be able to modify our code and integrate it easily with other open solutions.
4. Users should have total control over their data—they shouldn’t have to share private company information with us or anyone else to use our software.

After seeing how Kubecost was helping a growing number of teams, we decided to raise a $5 million seed round to pull together our founding team and build a company around the Kubecost open source project. Taking what we viewed as the best parts of Google’s culture (autonomy, open collaboration, and experimentation to name a few) and marrying them with our own values influenced by our open source roots (an emphasis on flexibility, allowing teammates to make decisions about how and where they work best, and optional meetings), we designed our company, Stackwatch, to be as developer-friendly as our product Kubecost was.

![The Kubecost team at Kubecon 2021](/assets/images/open-source-cost-management/image_1.jpg)

# Kubernetes at scale, community at the core: the future of Kubecost

Enterprises all over the world are now running containers, with more than 70% of Fortune 100 companies using Kubernetes, as shown in the last [Kubernetes Project Report](https://www.cncf.io/reports/kubernetes-project-journey-report/). As companies emerge from the early stages of their adoption journey and start to scale their efforts, many are looking at operating margins with an increasing focus on the impact from infrastructure and cloud bills. 

As a result, we’re now monitoring billions of dollars of cloud spend, and as our users move their implementation of Kubernetes to production, we’re partnering closely with them to give them control of spend—helping them build sustainable showback or chargeback models, offering governance solutions, real-time alerting, and more.

Open source is at the core of everything we build, as well as how we work, at Stackwatch. We couldn’t have built Kubecost without our deeply engaged community of users and open source contributors, and our core values of flexibility and neutrality inform every decision we make (starting with our commitment to building tools that are portable and cloud-agnostic).

It’s an exciting time for our company: we’ve just raised $25 million to take our products and team to the next level. Staying true to our mission of empowering engineers through access to meaningful, actionable data, we’re focusing on three key areas to [grow our team](jobs.kubecost.com) and help way more users:

* Expanding our open source contributions (exciting news on this topic soon!) and growing our community
* Creating a world-class user experience that doesn’t end at in-product interaction—we aim to truly partner with our customers to add real value, no matter where they are on their Kubernetes adoption journey
* Building new tools, more integrations, and different ways to implement Kubecost to reach an even broader audience of users

We’ll be sharing more in the coming weeks about our product roadmap and how you can help us build the future of Kubecost—our story is just beginning!
