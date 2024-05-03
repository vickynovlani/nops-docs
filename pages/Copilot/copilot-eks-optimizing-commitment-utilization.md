---
title: Our approach to optimizing commitment utilization 
keywords: savings, commitments, recommendations, nks, karpenter, compute copilot
tags: [copilot, eks]
sidebar: mydoc_sidebar
permalink: copilot-eks-optimizing-commitment-utilization.html
folder: Copilot
series: [Copilot]
weight: 1.0
---

### About Commitment Optimization

Commitment optimization is a feature of Compute Copilot for Karpenter, which allows it to effectively optimize utilization of pre-purchased commitments, such as reserved instances or savings plans, across an organization. In order to enable it on onboarded clusters, one of the Nodepools for each cluster has to be marked as a template. This can be done by selecting the ‘Use as template’ option during or after creation of the Nodepool.

### Input data 

nOps continuously monitors usage, compute savings plans, savings plans and reserved instances across all configured accounts of an organization. We run hourly metadata ingest jobs and build a point-in-time representation of usage and commitment utilization in an organization. This allows us to find cases of commitment underutilization and overutilization. Underutilization happens when more commitments are purchased than used. Overutilization is the opposite case and is a potential candidate for divestment to spot.

Additionally, for each configured cluster, we collect node metadata every five minutes. We collect information about node instance type, availability zone, platform and capacity type. This allows us to build a near real-time picture of usage that nOps manages in a cluster.

Optimization actions are performed at the intersection of sub-optimal commitments and usage we manage. For example, if we find out that there are unused RIs in us-east-1 but the clusters we manage are in us-west-2, we cannot do anything about that. Conversely, if the regions of the clusters and RIs match, we will try to divert usage in the cluster to cover the RIs.

### Mechanism of action

Compute copilot's main mechanism of action is creating and updating Karpenter Nodepools. For example, if it determines that there are spare RIs in the m7i family equivalent to 10 vCPUs, it will find or create a nodepool that targets m7i instance with a vCPU limit of 10 and at a higher priority (weight) than other Nodepools. 

If, in the next hour, it finds out that m7i is now over-utilized due to changing usage patterns elsewhere in the organization, Copilot will downadjust the Nodepool and terminate an appropriate number of m7i instances. This will lead to Karpenter creating instances in another family and/or capacity type. 

### How does Compute Copilot distribute capacity between multiple configured clusters?

If you have more than 1 configured cluster, Copilot will try to intelligently allocate spare commitment capacity between them. Copilot will first "over-allocate" by creating Nodepools in each cluster with a vCPU limit equal to the number of spare commitments. Afterwards, Copilot will monitor clusters to determine which clusters use up the allocated commitments. As soon as total utilization reaches the number of spare commitments, Copilot will readjust vCPU limits on all deployed Nodepools to prohibit any further instance creation. 


### How does Compute Copilot allocate spare commitments without specific region or family requirements?

In case if an underutilized commitment, for example, a Compute savings plan, does not have specific requirements for a region, family, platform or tenancy, Compute Copilot will try to allocate equivalent vCPUs to any deployed Nodepool with on-demand only capacity type. Similarly, if it is conceptually possible to merge multiple commitments, Compute Copilot will try to consolidate them in one Nodepool to avoid creating many Nodepools.

