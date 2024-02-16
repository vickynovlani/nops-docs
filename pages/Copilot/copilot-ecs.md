---
title: Compute Copilot for ECS
keywords: savings, recommendations, sharesave, ecs, copilot, autoscaling
tags: [copilot]
sidebar: mydoc_sidebar
permalink: copilot-ecs.html
folder: Copilot
series: [Copilot, Onboarding]
weight: 5.0
---


## About Compute Copilot for ECS and how it works <a id="about-compute-copilot-for-ecs-and-how-it-works"></a> ##

- Compute Copilot is a service that automatically optimizes any compute-based workload. It leverages ML algorithms to reduce your ECS costs by automatically migrating EC2 instances to Spot. 

- Compute Copilot Lambda is aware whenever ASG launches a new on-demand instance (such as in response to a desired capacity change). In response, it automatically launches a Spot instance with settings that mirror those of the on-demand instance, attaches it to the ASG, confirms it is in service, and removes the on-demand instance for you.


## Why Compute Copilot<a id="why-compute-copilot"></a> ##

- Compute Copilot uses AI-driven decision making to provision and run workloads at the cheapest price in real time, without manual effort.

- Compute Copilot allows you to benefit from Spot savings with the same reliability as On-Demand. By analyzing historical data and Spot Termination events, it ensures your critical workloads remain safe from interruption. 

- Compute Copilot does not require your workload to be transferred to a proprietary system, but works directly with AWS ECS. It does not typically modify the ASG settings, allowing it to be disabled at any time without interrupting existing workflows.


## Prerequisites<a id="prerequisites"></a> ##

1. You must be logged in to your [nOps account](https://app.nops.io/accounts/signin/). 

2. Your AWS account must be configured to your nOps account.

3. You must have the correct permissions. 

4. You must have an ECS cluster with ASG as a capacity provider. 


## Steps to Enable Managed Instance Draining via the AWS console<a id="steps-to-enable-managed-instance-draining-via-the-aws-console"></a> ##

1. Navigate to the AWS console -> ECS cluster -> Infrastructure -> Capacity Provider 

2. Select the ASG -> Update -> Expand Scaling policies -> Check the Managed instance draining\
   [Managed instance draining](https://aws.amazon.com/about-aws/whats-new/2024/01/amazon-ecs-managed-instance-draining/) is a new feature from and managed by AWS, which has been recently launched. It allows instances to drain tasks automatically.

   ![](https://lh7-us.googleusercontent.com/m--Q_mj_au0e7fopae8ZCqOk8RRJ7RKLutCh-IfGVoCy22o7Pf6eYzzmi9kyzsbgFq51CGLuGEBW2cdDAffHD-zkY5MGwlZpnk01tvdYiP9huWysNiy6fTd-Q-9ulos0w95QtpQepu2xSgoUvhyv2XY)

