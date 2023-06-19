---
title: Driving Freedom of Choice with a Flexible Kubernetes Infrastructure
author: Andy Clemenko, @clemenko, andy.clemenko@rancherfederal.com
---

# Driving Freedom of Choice with a Flexible Kubernetes Infrastructure

How making a few simple choices can drive freedom and flexibility.

---

> **Table of Contents:**
>- [Introduction](#introduction)
>- [Current Thinking](#current-thinking)
>- [New Strategy](#new-strategy)
>   - [Right Sizing](#right-sizing)
>   - [Improve Scaling](#improve-scaling)
>   - [Reduce Operational Costs](#reduce-operational-costs)
>   - [Better Focus on Problems](#better-focus-on-problems)
>- [Perfect Kubernetes Stack](#perfect-kubernetes-stack)
>- [Conclusion](#conclusion)
>- [Disclaimer](#disclaimer)

---

## Introduction

Throughout my career there has always been the struggle around complexity of systems. I seem to be talking about this more and more. The reason is that our infrastructure is getting more and more complex. While simultaneously adding more and more options. There has never been more choices for how and where to develop, build, and deploy applications. Just look at the job titles that are used today, Site Reliability Engineer (SRE), DevSecOps Engineer, and Cloud Engineer. It is really tough not to see every new technology in terms of [Gartner's Hype Cycle](https://www.gartner.com/en/documents/3887767).

![hype cycle](img/Gartner_Hype_Cycle.png)

As technologists, we should always be asking ourselves "How can we flatten the curves?". How can we make the technology easier, faster and more reliable? I had a Vice President of Sales once tell me "Andy, you have to dumb this shit down for me". I will never forget that statement. How can we flatten the curves for everyone?

## Current Thinking

The current trend is for companies, and governments, to leave the datacenter and head to the "cloud". Remember that the "cloud" is just someone elses computer. This trend has been very costly in the long run for many reasons. First and foremost are the technologies that need to be adopted to validate/simplify the move. Infrastructure as code is one of the technology, or core concepts, for a highly effective transition to the "cloud". The problem comes in when trying choose the right tool for the right job. Case in point, The Amazon Prime Video team published an [article](https://www.primevideotech.com/video-streaming/scaling-up-the-prime-video-audio-video-monitoring-service-and-reducing-costs-by-90) about how they saved money and improved performance by migrating away from Lamda. This article highlights a trend, that is showing up more and more, of moving back toward traditional monolithic software/system design. In response to the article [Adrain Cockcroft](https://adrianco.medium.com/so-many-bad-takes-what-is-there-to-learn-from-the-prime-video-microservices-to-monolith-story-4bd0970423d4) has a great quote.

> *So maybe the answer to the question of whether to build with microservices or a monolith is neither, you should be calling an existing service rather than rolling your own.*

I love the idea and simplicity of looking before building. Adding costs into the equation is another major headache for companies/governments. A few years ago Dropbox started a [Reverse Migration](https://www.datacenterknowledge.com/manage/dropbox-s-reverse-migration-cloud-own-data-centers-five-years) from the cloud to back on premise. Cost's was one of the major factors that drove this decision. In fact there are dozens, if not hundreds, of [Cloud Cost Optimization Companies](https://www.cloudzero.com/blog/cloud-cost-management-tools). An entire industry was built around the complexity of cost around the cloud providers. All of this makes you start to think if the "cloud" is a bad idea. Have you ever seen a mechanic moving their toolbox?

![tow truck](img/tow_truck.jpeg)

This is a simple analogy for moving to the cloud and back.
The answer is a little more complicated and nuanced. This is where the new strategy takes shape.

NEEDS WORK

## New Strategy

Let's call the new strategy "right toolbox". The basic is idea follows what [Adrain Cockcroft](https://adrianco.medium.com/so-many-bad-takes-what-is-there-to-learn-from-the-prime-video-microservices-to-monolith-story-4bd0970423d4) wrote. It is around having a large enough toolbox to be able to pick the right tool for the job. While not trying to build the biggest toolbox around. Let's focus in on the Kubernetes ecosystem. Applying the "right toolbox" strategy really means looking at a few tools in each of the different product categories. Obviously we are big fans of the Rancher stack.

![rancher stack](img/rancher_stack.jpg)

One of the key takeaways is that you can pick and choose what tools you want to use at all the different layers. Meaning, you can use any operating system. Any infrastructure. Any storage layer. Why is this important? Freedom.

### Right Sizing

One of the biggest trends that we are seeing lately is the capability of edge computing. The trend is really following the idea of data locality. This is where it is more efficient to compute where the data is generated or captured. This is really coupled with the power of modern CPUs, memory, storage and even GPUs. Having a flexible stack means you can use the same applications that are destined for the data center on the edge. For reference we published an article about [Deploying at the Edge with Kubernetes](https://intelligencecommunitynews.com/ic-insiders-tactical-edge-reference-architecture/) highlighting the capability of the modern edge. For sizing clusters, using the "right toolbox" strategy means not relying on the cloud provider specific tooling for scaling and deploying.

### Improve Scaling

Looking at scaling more closely we can take advantage a tool like Rancher. [Rancher](https://www.rancher.com/products/rancher), in short, is a Secure Multi-Cluster Manager that can manage cluster lifecycles on any cloud provider. This enables significantly easier scaling within a single provider, or even to multiple providers. The cool advantage of multiple cloud providers is that there is an increased opportunity in migrating for cost or data locality.

### Reduce Operational Costs

Speaking of cost, there are a few ways where the "right toolbox" can help. For starters, being able to eliminate costly tools that not needed. Secondary is not having to carry the tech debt from those tools. Third is the abstraction away from the cloud vender specific tooling. Think about the cost of vendor lock when using their tools at every level of the stack.

### Better Focus on Problems

We are starting to see new trends in even abstracting away kubernetes. [Acorn Labs](https://www.acorn.io/microservices-are-dead-long-live-the-monolith/) has a great article about how microservices are dead. Being able to abstract away a layer of the infrastructure has some great advantages.

## Perfect Kubernetes Stack

We have a nice [Raference Architecture for the Rancher Stack](https://github.com/clemenko/rancher-ref-arch) that will help with some of the specifics. For me, the perfect stack is one that will be malleable to as many situations as possible. One that can live nicely in a cloud or at the tactical edge. A stack that I can swap add a GPU or disconnect from the internet and know it will remain performant and reliable. We think using as many of the Rancher components as possible is the best idea. ;) Some of the underlying principles for Rancher is security and interoperability. Rancher and RKE2 ( Kubernetes ) both have DISA Security Technical Implementation Guides (STIGs). We have several articles that go in depth on [NSA Hardening Guide](https://intelligencecommunitynews.com/ic-insiders-creating-a-secure-kubernetes-deployment-five-ways-the-new-nsa-kubernetes-hardening-guide-can-help/) and the [STIG Guidance](https://intelligencecommunitynews.com/ic-insiders-have-you-stigd-your-kubernetes-yet/). With all the security in mind, my "perfect stack" looks like:

- Hardware - [Dell R6615 AMD Epyc Server](https://www.dell.com/en-us/shop/servers-storage-and-networking/poweredge-r6615-rack-server/spd/poweredge-r6615/pe_r6615_16729_vi_vp) - Several 1Us for HA
- HyperConverged - [Harvester](https://www.rancher.com/products/harvester) - VMs and containers
- VM OS - [Rocky Linux 9](rockylinux.org) - SELINUX support
- Kubernetes [RKE2](https://www.rancher.com/products/rke) - Security Focused Kubernetes
- Storage - [Longhorn](https://www.rancher.com/products/longhorn) - Uses storage already present
- Multi-Cluster Management - [Rancher](https://www.rancher.com/products/rancher) - Manages Application and Cluster Lifecycles
- Security - [Neuvector](https://neuvector.com/) - Proactive Security & Observability

I would deploy everything with Infrastructure as Code (IaC) principles. This will give us the ability to deploy to any cloud, any where, and at any time.

## Conclusion

The "right toolbox" strategy is the perfect toolbox. Having just the right amount of tools reduces cognitive load and empowers your team. Plus the right tools make jobs easier.

![small toolbox](img/toolbox.jpg)

Does Rancher and it's stack help flatten the curve? Being able to provide a some abstraction from the cloud provider will increase choice and freedom.

## Disclaimer

> "This publication was prepared or accomplished by the author in a personal capacity. All opinions expressed by the author of this publication are solely their current opinions and do not reflect the opinions of Rancher Federal, Inc., respective parent companies, or affiliates with which the author is affiliated. The author's opinions are based upon information they consider reliable, but neither Rancher Federal, Inc., nor its affiliates, nor the companies with which the author is affiliated, warrant its completeness or accuracy, and it should not be relied upon as such."
