---
title: Getting Started with nSwitch Essentials
keywords: savings, recommendations, sharesave, essentials
tags: [savings, recommendations, sharesave]
sidebar: mydoc_sidebar
permalink: essentials-overview.html
folder: ShareSave
---

## nSwitch Essentials

The nSwitch Essentials module will enable you to automate the laborious task of changing candidate volumes from gp2 to gp3 volumes via EventBridge or nSwitch Changeset (for those gp2 volumes that are defined in your terraform configuration file), allowing you to stay focused on innovation.


nSwitch Essentials integrates with Git and Terraform to streamline the process of identifying and fixing code related to storage optimization. 


Utilizing nOps’ certified integration with Amazon EventBridge, nSwitch Essentials can intelligently update configurations on resources that are not controlled by Infrastructure as Code (IaC). 

Read more about essentials in our [Essentials feature release blog post announcement](https://www.nops.io/blog/nops-announces-nswitch-essentials-for-cloud-storage-optimization/).


## Pre-Requisites ##
Dy default, AWS has a soft limit of 50TB in gp3 EBS Volumes per region per account.  Eceeding that limit with a migration through EventBridge will cause the migration to fail.

### Increasing EBS service quote ###
To ensure migration from gp2 to gp3 is successful, we recommend using the AWS [Service Quota Console](https://console.aws.amazon.com/servicequotas/home) to request increases for your accounts.

1. [Navigate to the EBS service](https://console.aws.amazon.com/servicequotas/home/services/ebs/quotas) in the quota console.
1. Search for gp3.
1. Select the radio button for [Storage for General Purpose SSD (gp3) volumes, in TiB](https://console.aws.amazon.com/servicequotas/home/services/ebs/quotas/L-7A658B76) and click _**Request quota increase**_.

    ![](/tmpimg/storagequota001.png)
1. In the Change quota box, enter in the total amount that you want the quota to be.
    ![](/tmpimg/gp3_enter_quota.png)
1. Click _**Request**_.
1. Repeat this for each region and account for which you are planning on migrating gp2 to gp3.








## Enabling Essentials for EventBridge ##
=====================

For each Event Bridge you configure, log into the corresponding AWS account first.

![](/tmpimg/essentials001.png)

1. Click on your name to the top right of nOps.
2. Organization Settings.
3. Under Settings, Integrations.
4. Click on the Event Bridge tab.
5. For the Essentials line item, Launch Stack.
6. In the tab that pops up, run the CloudFormation stack.
7. Confirm the stack completes successfully.
8. Return to nOps to create your nSwitch Essentials schedule.

