---
title: Onboarding your EKS clusters to Copilot for EKS Cluster Autoscaler
keywords: savings, recommendations, sharesave, nks, karpenter, compute copilot
tags: [savings, recommendations, sharesave, eks, nks, copilot]
sidebar: mydoc_sidebar
permalink: copilot-eks-cas-guide.html
folder: Copilot
series: [Copilot, Onboarding]
weight: 1.0
---


# Enabling Compute Copilot for EKS Clusters with Cluster Autoscaler: Onboarding Guide

# **About Compute Copilot for Cluster Autoscaler and how it works**

Compute Copilot is a powerful service designed to automatically optimize compute-based workloads, reducing costs on AWS EKS by intelligently migrating EC2 instances to Spot instances using machine learning algorithms.

*Cluster Autoscaler* is a key feature that dynamically adjusts the number of nodes in a node group within an EKS cluster to accommodate changes in resource requirements for pods. When a scaling decision is made, Cluster Autoscaler communicates with the associated Auto Scaling Group (ASG) to adjust the **`DesiredCapacity`**, prompting the ASG to automatically scale the cluster nodes.

Here's how it works:

1. **Scaling Operation:** Cluster Autoscaler triggers a scaling operation by adjusting the **`DesiredCapacity`** of the ASG.
2. **Compute Copilot Lambda Activation:** Whenever the ASG launches a new on-demand instance (e.g., in response to a desired capacity change), the Compute Copilot Lambda is activated.
3. **Spot Instance Launch:** The Compute Copilot Lambda responds by automatically launching a Spot instance configured to mirror the settings of the on-demand instance.
4. **Attachment to ASG:** The Spot instance is seamlessly attached to the ASG, confirming its serviceability.
5. **On-Demand Instance Removal:** Simultaneously, the Compute Copilot Lambda removes the corresponding on-demand instance, completing the migration process.

Moreover, when Compute Copilot Lambda needs to replace an on-demand instance associated with an EKS Cluster, it communicates with the Compute Copilot Agent running in the cluster. This ensures a graceful removal of pods from the node before termination, preserving the integrity of your EKS environment.

By combining the automation capabilities of Cluster Autoscaler with the intelligent instance management of Compute Copilot, this solution offers a seamless and cost-effective approach to optimizing AWS EKS workloads and reduce costs.

# Prerequisites

1. You must be logged in to your [nOps account](https://app.nops.io/accounts/signin/).
2. Your AWS account must be configured to your nOps account.
3. You must have an EKS Cluster with Cluster Autoscaler installed.

# ****Steps to Configure Your EKS Cluster for Cost Optimization and Savings****

{%include important.html content="
The EKS Dashboard distinguishes clusters utilizing Cluster Autoscaler by representing them in orange, while clusters employing Karpenter are represented in blue. For learning how to configure clusters that use Karpenter, please, refer to this [this documentation](https://help.nops.io/copilot-eks-onboarding.html)."%}


## Install Compute Copilot Lambda

For instrunctions on how to install Compute Copilot Lambda, please, refer to [the Compute Copilot for Auto Scaling Groups (ASG) documentation](https://help.nops.io/copilot-asg-onboarding.html?#prerequisites).

## Install Compute Copilot Agent

1. Navigate to Compute Copilot → EKS from the nOps dashboard.
2. Choose the EKS cluster you want to cost-optimize.
3. Open detail view by clicking on →.
4. Generate a new API key for nOps Agent.
5. Copy the custom command and run it in your command line.
6. Test Connectivity of Compute Copilot Agent in the Compute Copilot for EKS Dashboard.

    ![ezgif-2-c7f3b8d28c.gif](/tmpimg/ezgif-2-c7f3b8d28c.gif)

## Configure ASGs associated with the Cluster

1. Navigate to the EKS Dashboard and select an EKS cluster that uses Cluster Autoscaler.
    - Open Configure Model of the ASG you want to configure. The details section of Auto Scaling Group will be prefilled.
    - The AWS Lambda configuration section will show the version detail and current status of the Lambda Stack to confirm it is properly configured on the AWS account.
    - You can create or choose an existing ASG template in the Spot detail section.
2. Create an ASG Template.
    - Give the ASG template a unique name
    - Choose the instance families, vCPU, and Memory suitable for your workload. From this pool, Compute Copilot will select the most optimal choice for price and stability.
    - It is recommended to select as many instance families as possible, to provide Compute Copilot with a wider recommendations pool.

    ![ezgif-2-c7f3b8d28c.gif](/tmpimg/ezgif-2-c7f3b8d28c%201.gif)


{% include custom/series_related.html %}