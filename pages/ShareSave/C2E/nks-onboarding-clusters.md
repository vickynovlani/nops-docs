---
title: Onboarding your EKS clusters to nKS
keywords: savings, recommendations, sharesave, nks, karpenter, compute copilot
tags: [savings, recommendations, sharesave, eks, nks]
sidebar: mydoc_sidebar
permalink: nks-onboarding-clusters.html
folder: ShareSave
---

## Onboarding your EKS clusters to nKS ##

### Pre-requisites: ###

1. You must be logged in to your [nOps account](https://app.nops.io/accounts/signin/). 
2. Your AWS account must be configured to your nOps account.
3. You must have Kubernetes cluster with Karpenter installed.

### About nKS: ###

Karpenter offers significant advancements in intelligent scaling, cluster awareness, and customization. However, it is often tuned as a one-and-done — whereas your ecosystem and market pricing are constantly changing. 

That’s where nKS (nOps Karpenter Solution) comes in, constantly tuning your configuration for the best price and availability on autopilot. It allows engineering teams to take advantage of Karpenter’s more effective and granular scaling functionalities, for a fraction of the effort. 

nKS ensures you are scheduled on the most cost-optimized and stable option at every moment — automatically updating your provisioning on the fly if not for 50+% EKS savings.

### Why nKS over legacy Autoscaler: ###

Optimizing your AWS costs is a key challenge today. Spot can be cheaper, but terminations pose the threat of outages to your critical workloads. RIs and Savings Plans require risky, long-term commitment and can lead to paying for capacity you don’t need.

nKS continuously rightsizes, reconsiders, and re-evaluates your workload placement to available RIs, SPs, or Spot to maximize your savings on autopilot with complete reliability. It is aware of your entire dynamic AWS ecosystem and market pricing in real time. 

nKS even covers your commitments with a 100% money-back guarantee. If your usage changes, you change instance regions, or even leave the cloud, we buy back those commitments from you. You get all the cost savings of commitments, with all the flexibility of on-demand. In contrast, Cluster Autoscaler requires much more of your time and labor, lacks Karpenter’s advanced autoscaling automation, and makes you choose between cost savings and flexibility.

## Steps to Configure Your EKS Cluster for Cost Optimization and Savings ##

### Install nOps Agent: ###

1. Navigate to nKS from the nOps dashboard.
2. Choose the EKS cluster you want to cost-optimize.
3. Open detail view by clicking on →.
4. Generate a new API key for nOps Agent. 
5. Copy the custom command and run it in your command line. 
6. Test Connectivity of nOps Agent in the nKS Dashboard.

    ![](https://lh4.googleusercontent.com/7eISgP_ZiLo_JO2zGS8dOdp7HvYLBO4N5rMK1FC-szbc668pp-pCz_ysW2NKhvPylazv_3oRIden3mwgLG09eWT0XsbXX31dfsJ_Sot5PpBSJERDAsErwjI_wQC8kRseM_ezcQZ7JxzR05e8Gtdz328)

### Create Node Template: ###

1. For the selected EKS cluster, create a Node Template.
2. Assign a unique name to the Node Template.
3. Choose the AMI Family from the dropdown menu.

    ![](https://lh3.googleusercontent.com/PAwzhjL32w7WQnqUctFgu6vdhTZxa1k8VBeour0tuKF-3Fh8-2T8u5gcd2nzzukT7mhe12BKjkeAO9wsv9XsCjewXzfeLRngVdDevGOpii7v2pFi_l2mIWy4ldO-hSrkwJCs4HbkTV3Qs73tufsibKk)

4. Add Subnet IDs manually or with Search by tags. 
5. Add Security Group IDs manually or with Search by tags 
6. Select IAM Role or use default Karpenter IAM Role

    ![](https://lh3.googleusercontent.com/uxZn7EekvWOJ_6ucFrNoI5A1VQIOwLVy46vYNyHdhycQIIQLxxOFsHSuoM7bp4rDToBMrK4OxJdj70aoRXgX_IfEJDz0LxuSKW8zzUEdh9WklomEBMPZ8Pp6u5BJb0850YjG_pvY8kWEL2ECeNAdIz4)

7. Configure Metadata Options with user data to give commands after node starts \[optional].
8. Create Device Mapping by providing necessary details \[optional].
9. Create Node Template.

    ![](https://lh5.googleusercontent.com/SP1sgMPmewYKjLGAK2JuOQ5HVYD6F2KFXgTbQIzrnyli_FflSsyh_AJtyv0RZQeud8c6Ns-aNK-sn1qC_O7JuNkVaoV_ackSRriFDbhqadtxc_l5InMnZpXnyFaHsGkbOnhYMob_tf3BJ3eV155g390)

{%include note.html content="you can create multiple node templates"%}

### Create Provisioner: ###

1. Assign a unique Provisioner name.
2. Select the created Node Template to pull configuration from.
3. Select Availability Zones.
4. Select Capacity Type — Spot, On Demand or both \[recommended to select both]

    ![](https://lh6.googleusercontent.com/2mI3pZSbhuJE3VPcmNPJF_TYHC2_0RLC2kNP9zOvdItw5_V9HrdOlPnkVUT-v1hEdCNGXublDDLmW6n_aUdg8Vffz03EEz0c-9j1MmqY4KnqU2JQ9JUQLEJkdDyd1MiqO1N76ZeNQi-U9218KL68xHA)

5. Select Max Limit of vCPUs & Memory.
6. Create Tents and Labels if required \[for specific provisioner service].
7. Choose the range of vCPUs and Memory for the instance.
8. Select the appropriate instance family.
9. Create Provisioners. 

    ![](https://lh6.googleusercontent.com/-xWeSOU5AjLrwx4766WSqXCYeKWq75IjApmZOYgPqkbqbSViB9sy1djBCEFF22cN0sS-SF7KEzyHCcO-S2tcdsZh2bFlro_GZTNTR6w9uN1yYRvS4JHvW6iWRmlKDMducQLL9yYr4V30fi2RUfGynoE)

{%include note.html content="You can create multiple Provisioners, but each Provisioner will have only 1 Node Template" %}

Once the Provisioner is created, the user can again Test Connectivity to confirm that the  EKS cluster is configured correctly.

![](https://lh5.googleusercontent.com/1XtlFL95uQrrw0ZVXZqXixK67rP3TkHd6C7nC6t-1_yoCHhtRtk72cWk1axUaY1O4jCptHt_fU65qUun0wB2UGS7QdWhUwdvZ50_YCpPCAuRGZ9Ccvr6UJVYk1Onca79LysK6gudT4WA8Tj2SV5NL4c)

     

As soon as cluster status displays **Configured**, nKS will start its magic to generate savings on the connected EKS cluster. 

FAQ:

1. Nks provisioner takes precedence over clients own provisioner?
2. IaC/YAML template for configuring nKS?
3. Helping customers with Karpenter migration/devOps support?
