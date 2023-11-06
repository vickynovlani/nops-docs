---
title: Getting Started with ShareSave
keywords: savings, recommendations, sharesave, nswitch, nks, ec2, rds
tags: [savings, recommendations, sharesave]
sidebar: mydoc_sidebar
permalink: sharesave-overview.html
folder: ShareSave
series: [ShareSave, Savings]
weight: 30
---

# Getting Started with ShareSave

The nOps' ShareSave module provides risk-free EC2 and RDS commitment management.  It's ideal for organizations that are growing rapidly and are having difficulties keeping track of everything ranging from server side, CMS stack, API stack, analytics, to linear playout engine.

ShareSave is also ideal for organizations that, during their rapid expansion, over-buy reserved instances at an alarming rate to keep up with the demands and it is now difficult for them to wind down after everything settles. ShareSave can not only help during their expansion but also helps save a substantial percentage on monthly AWS costs with the help of ShareSave Risk-Free Commitment Management, nSwitch Scheduler, nSwitch Essentials, and nKS.

## ShareSave Automations ##
=====================

The following is the list of cost-saving automation under ShareSave:

*   [nSwitch Essentials](essentials-overview.html)
*   [nSwitch Resource Scheduler](https://www.nops.io/sharesave-scheduler-overview/)
*   [nKS](https://www.nops.io/nks/)
*   [Risk-Free Commitment Management](https://www.nops.io/sharesave-overview/)
    

### Storage Essentials ###
Switching EBS volumes from gp2 to gp3 to reduce storage costs.


### nSwitch Resource Scheduler ###
nOps ShareSave Resource Scheduler makes it easy to pause resources (EC2 instances, EC2 Autoscaler clusters, RDS instances, RDS clusters, and EKS noegroups) during inactivity and leverages the Amazon EventBridge bus to deliver signals to resources to stop them during inactivity and start them when they are most likely to be used automatically.  It can also pause non-production workloads during off-hours.


### nKS ###
nKS schedules your EKS workloads on the most cost optimal option for your environment in real-time. By integrating Karpenter with nOps' engine, it streamlines the management of RIs, Savings Plans, and Spot resources with ML-driven cost optimization.

### Risk-Free Commitment ###
Real-time, risk-free, hands-free automatic life-cycle management of Amazon EC2 and RDS commitments.

The ShareSave AI engine collects Amazon CloudWatch and AWS CloudTrail logs and continuously monitors and analyzes infrastructure usage data points. It then automatically reacts in real time by purchasing RIs upon an increase in compute usage and selling RIs upon a decrease in compute usage. nOps continuously purchases and sells commitments on an hourly basis, depending on your infrastructure’s capacity changes.

ShareSave grabs the most lucrative discounts in the Amazon EC2 Reserved Instance Marketplace.


## ShareSave Dashboard ##

The Sharesave Dashboard provides clear visibility of the potential savings that can be achieved using the nOps Platform. The ShareSave program is able to process 6 months' worth of data.

nOps continually refines its savings recommendations and strives to take ShareSave to absolute perfection.

The ShareSave Dashboard consists of three sections:

1.  Savings Summary and Breakdown
    
2.  List of Opportunities
    
3.  Filter
    

### Savings Summary and Breakdown ###

In the Savings Summary, you will find:

*   **Lost Opportunities —** Money you could have saved, if you had signed up for nOps ShareSave, in the last 60 days.
    
*   **Estimated Total Saving —** Estimated saving nOps ShareSave for the specified time period (MTD, 7 Days, 30 Days, 60 Days, 90 Days).
    
*   **Estimated Total ShareSave Fee —** What we will charge for saving your money.
    
*   **Estimated NET Savings —** What you Save after paying nOps.
    
*   **Net Savings % —** The percentage of costs that you saved vs on-demand
    
*   **Estimated Annualized Net Savings —** What you will save in a year with ShareSave (Estimated savings vs on-demand with ShareSave).
    

![](/tmpimg/sharesave-summary.png)

You can also select the following tabs within the **Saving Summary and Breakdown** section to see a graphical representation and breakdown of your savings with respect to date and opportunity type:

*   Total Savings
    
*   Total ShareSave Fee
    
*   Net Savings
    
*   Annualized Net Savings
    

### List of Opportunities ###


The **List of Opportinities** consists of the following list:

*   nSwitch Essentials
    
*   EC2 nSwitch Scheduler
    
*   RDS nSwitch Scheduler
    
*   nKS
    
*   Risk-Free Commitments

On the left side menu, you can filter to one or more Opportunity Type.

#### nSwitch Storage Essentials ####

In **nSwitch Storage Essentials** section, click expand the list of cost saving migrations from gp2 to gp3 EBS Volume type:

![](/tmpimg/sharesave-essentials-list.png)

#### Amazon Elastic Compute Cloud ####

In **Amazon Elastic Compute Cloud** section, click on _EC2 nSwitch_ to expand the list and see the details including instance type, account name, region, total savings, and **Create**:

![](/tmpimg/sharesave-ec2nswitch-list.png)

Click on the **Create** button to the right of an opportunity to create an automated schedule to turn the instance on and off with the help of EventBridge. 


#### Amazon Relational Database Service ####

In the **Amazon Relational Database Service** section, click on an opportunity name to expand the list and see the details including resource name, RDS type, instance size, account name, region, total savings, and **Create**:

![](/tmpimg/sharesave-rdsnswitch-list.png)

Click on the **Create** button to the right of an opportunity to create an automated schedule to turn the instance on and off with the help of EventBridge. 

#### nKS ####

In the **nKS** section, click on an opportunity name to expand the list and see the details including EKS cluster name, instance type, account name, region, total savings, and **Configure**:

![](/tmpimg/sharesave-nks-list.png)

Click on the **Configure** button to the right of an opportunity to start the configuration process for the nKS module. 



#### List of Risk-Free Commitments ####

Actions against the List of Risk-Free Commitments are automatic and are carried out by the nOps ShareSave AI.

In the **Risk-Free Commitment** section, click on an opportunity name to expand the list and see the details including resource name, account name, region, previous configuration, suggested configuration, detection date, and total savings:

![](/tmpimg/sharesave-opp-list.png)


### Filters ###
-------

Use the **Filter** section, to apply filters on the entire ShareSave dashboard based on the selected cloud accounts and opportunity types:

![](/tmpimg/sharesave-filters.png)

## Prerequisites ##
=============

You must have access to your _AWS Master Payer Account ID_. With this ID, we will be able to generate a $0 Market Place Private Offer (MPPO) and send it over to you, or you can accept the Marketplace Public Offer. 

nOps recommends that you configure your AWS accounts to nOps with [Automatic Setup](onboarding-aws-with-automatic-setup.html) for your payer account and [Multi-Account Setup with CloudFormation](onboarding-aws-with-cloudformation.html) to configure linked accounts.

If you are an existing nOps customer, in order to get access to all the cost saving features of ShareSave, you might need to update the IAM permissions for nOps. To update the IAM permissions:

1.  Log into your nOps account.
    
2.  Click on your profile name in the top right corner.
    
3.  Navigate to the **IAM Policy Update** section. You will see a list of your AWS accounts associated with nOps.
    
4.  Click the **Update on AWS** button against your master payer account. Make sure that you are already logged in to your master payer account before you click the button.
    
5.  Click the **Update on AWS** button against all associated accounts. Make sure that you are already logged in to the respective AWS account before you click the button **(optional)**.
    
Follow the steps to configure [Risk-Free Commitment Management](/rfcm-configure.html)


{% include custom/series_related.html %}