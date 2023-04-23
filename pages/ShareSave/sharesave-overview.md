---
title: Getting Started with ShareSave
keywords: savings, recommendations, sharesave
tags: [savings, recommendations, sharesave]
sidebar: mydoc_sidebar
permalink: sharesave-overview.html
folder: ShareSave
---

# Getting Started with ShareSave

#### ShareSave provides risk-free Auto-pilot EC2, RDS, ElasticCache, OpenSearch, and Redshift Reserved Instances Management. ####


ShareSave is ideal for organizations that are growing rapidly and are having difficulties keeping track of everything ranging from server side, CMS stack, API stack, analytics, to linear playout engine.

ShareSave is also ideal for organizations that, during their rapid expansion, over-buy reserved instances at an alarming rate to keep up with the demands and it is now difficult for them to wind down after everything settles. ShareSave can not only help during their expansion but also helps save a substantial percentage on monthly AWS costs with the help of ShareSave RI management, ShareSave Scheduler, and ShareSave Graviton programs.

## ShareSave Automations ##
=====================

The following is the list of cost-saving automation under ShareSave:

*   [Risk-Free Commitment](https://www.nops.io/sharesave/)
    
*   Graviton
    
*   [nSwitch Resource Scheduler](https://www.nops.io/sharesave-scheduler-overview/)
    
*   Amazon Relational Database Service
    

### Risk-Free Commitment ###
--------------------

Real-time, risk-free, hands-free automatic life-cycle management of Amazon EC2 and RDS commitments.

The ShareSave AI engine collects Amazon CloudWatch and AWS CloudTrail logs and continuously monitors and analyzes infrastructure usage data points. It then automatically reacts in real time by purchasing RIs upon an increase in compute usage and selling RIs upon a decrease in compute usage. nOps continuously purchases and sells commitments on an hourly basis, depending on your infrastructure’s capacity changes.

ShareSave grabs the most lucrative discounts in the Amazon EC2 Reserved Instance Marketplace.

### Graviton ###
--------

Switching workloads to AWS Graviton-based instances that provide the best price-performance for workloads in Amazon EC2.

### Resource Scheduler ###
------------------

nOps ShareSave Resource Scheduler makes it easy to pause resources during inactivity and leverages the Amazon EventBridge bus to deliver signals to resources to stop them during inactivity and restart them when they are most likely to be used automatically.


### Amazon Relational Database Service ###
----------------------------------

The RDS recommendations clearly describe the optimization approach you should take and shows the recommendations to implement.

nOps looks at the utilization metrics and determines time periods when RDS instances are running but are inactive. The insights that nOps gather from your utilization partners turn into scheduling recommendations that you can implement to immediately start savings and reducing your spend.

## ShareSave Dashboard ##
===================

The Sharesave Dashboard provides clear visibility of the potential savings that can be achieved using the nOps Platform. The ShareSave program is able to process 6 months' worth of data.

nOps continually refines its savings recommendations and strives to take ShareSave to absolute perfection.

The ShareSave Dashboard consists of three sections:

1.  Savings Summary and Breakdown
    
2.  List of Opportunities
    
3.  Filter
    

### Savings Summary and Breakdown ###
-----------------------------

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
---------------------

The **List of Opportunities section** consists of the following list:

*   List of Risk-Free Commitments
    
*   List of Graviton
    
*   Resource Scheduler
    
*   Auto Scaling Groups
    
*   Amazon Relational Database Service
    

### List of Risk-Free Commitments

Actions against the List of Risk-Free Commitments are automatic and are carried out by the nOps ShareSave AI.

In the **List of Risk-Free Commitment**, click on an opportunity name to expand the list and see the details including resource name, account name, region, previous configuration, suggested configuration, detection date, total savings, and action:

![](/tmpimg/sharesave-opp-list.png)

#### List of Graviton

In the **List of Graviton**, click on an opportunity name to expand the list and see the details including resource name, region, previous configuration, suggested new configuration, detection date, and total savings:

![](/tmpimg/sharesave-opp-ri-list.png)

#### Resource Scheduler

In **Resource Scheduler,** click on an opportunity name to expand the list and see the details including instance type, account name, region, schedule name, new configuration, confidence level, total saving, and action:

![](/tmpimg/sharesave-nswitch-list.png)

Click on the **Schedule** button against an opportunity to create an automated schedule to turn the instance on and off with the help of EventBridge. To learn more about nSwitch see [Utilize nOps Resource Scheduler with EventBridge Integration to Reduce Costs Automatically](solutions-using-eventbridge-with-nswitch-to-reduce-costs.html).


#### Amazon Relational Database Service

In the **Amazon Relational Database Service**, click on an opportunity name to expand the list and see the details including resource name, RDS type, instance size, account name, region, current schedule, recommended schedule, total savings, and action:

![](/tmpimg/rds-nswitch.png)

Click on any opportunity name to see the details of the resource and its usage pattern:

![](/tmpimg/rds-metrics.png)

To schedule a recommendation, click the **Schedule** button against the recommendation. If you click the Schedule button, you will see two options:

*   Create New Schedule
    
*   Attach Existing Schedule
    

To create a new schedule, based on the nOps recommendation, click **Create New Schedule**, all fields will be prepopulated according to the recommendation. Simply click **Create** to start reducing your spend:

[![](https://downloads.intercomcdn.com/i/o/656927495/b56fce700e6c94203118ca76/2023-01-21_20-31-14.png)](https://downloads.intercomcdn.com/i/o/656927495/b56fce700e6c94203118ca76/2023-01-21_20-31-14.png)

To attach an existing schedule to the RDS resource(s), click the **Attach Existing Schedule** button, select an existing schedule from the dropdown list, and click **Attach**.

![](/tmpimg/create-schedule.png)

### Filters ###
-------

Use the **Filter** section, to apply filters on the entire ShareSave dashboard based on the selected cloud accounts and opportunity types:

![](/tmpimg/sharesave-filters.png)

## Prerequisites ##
=============

You must have access to your _AWS Master Payer Account ID_. With this ID, we will be able to generate a $5 Market Place Private Offer (MPPO) and send it over to you. It's very easy to accept the offer and onboard an account.

nOps recommends that you link your AWS accounts to nOps with [Automatic Setup](onboarding-aws-with-automatic-setup.html). If you are an advanced AWS user and have specific requirements, you can also link your account to nOps with [Manual Setup](onboarding-aws-with-manual-setup.html), [Multi-Account Setup with Terraform](onboarding-aws-with-terraform.html), and [Multi-Account Setup with CloudFormation](onboarding-aws-with-cloudformation.html).

If you are an existing nOps customer, in order to get access to all the cost saving features of ShareSave, you might need to update the IAM permissions for nOps. To update the IAM permissions:

1.  Log into your nOps account.
    
2.  Click on your profile name in the top right corner.
    
3.  Navigate to the **IAM Policy Update** section. You will see a list of your AWS accounts associated with nOps.
    
4.  Click the **Update on AWS** button against your master payer account. Make sure that you are already logged in to your master payer account before you click the button.
    
5.  Click the **Update on AWS** button against all associated accounts. Make sure that you are already logged in to the respective AWS account before you click the button **(optional)**.
    

## ShareSave Configuration ##
=======================

In the scope of this document, we will go through the configuration of **ShareSave - List of Risk-Free Commitments**.

To learn about **ShareSave - nSwitch Resource Scheduler** and its configuration, see [Utilize nOps Resource Scheduler with EventBridge Integration to Reduce Costs Automatically](solutions-using-eventbridge-with-nswitch.html).

To configure **ShareSave - List of Risk-free Commitment**, follow these steps:

1.  Log in to your nOps environment and head over to the **ShareSave** dashboard:
    
 ![](/tmpimg/sharesave-menu.png)
    
2.  On the **ShareSave** dashboard, in the **List of Opportunities** section, click the **Configure Risk Free Commitment** button:
    
    ![](/tmpimg/configure-rfcm.png)
    
    1.  If your account has already been configured, you won’t see the **Configure Risk Free Commitment** button. The button is only visible to new customers and existing customers who haven't configured ShareSave yet.
        
    2.  _Risk Free Commitments_ are only available to customers that onboard a Master Payer Account. You will not see the button if you haven’t onboarded a Master Payer account.
        
    
3.  Once you click the **Configure Risk Free Commitment** button, the following pop-up will appear:
    
    ![](/tmpimg/rfcm-proceed.png)
    
    1.  If the pop-up does not appear, make sure that the pop-up isn’t being blocked by your browser.
        
    2.  Before you click **Proceed,** make sure that you're logged in to your AWS master account in the same browser.
        
    
4.  After you click **Proceed**, nOps will take you to your AWS console’s CloudFormation **Quick create stack** page —with all the required information pre-filled— in order to create the required Cost and Usage Report (CUR). **Acknowledge** and click **Create stack**:
    
    ![](/tmpimg/rfcm-stack.png)
    

**ShareSave - List of Risk-Free Commitments** configuration is now complete.

* * *

**Note:** It will take upto 24 hours for the data to populate in nOps.

* * *
