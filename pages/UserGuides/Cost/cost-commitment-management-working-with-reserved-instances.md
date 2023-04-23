---
title: Commitment Management - Working with Reserved Instances
keywords: cost reporting, cost history, cost allocation
tags: [cost_visibility, reporting, savings]
sidebar: mydoc_sidebar
permalink: cost-commitment-management-working-with-reserved-instances.html
folder: UserGuides
---

# Commitment Management - Working with Reserved Instances #

## Managing and viewing AWS Reserved Instances via Commitment Management Dashboard ##


nOps enables you to view usage of AWS Reserved Instances on a near-real-time basis. Reserved instances provide significant cost savings compared to on-demand billing, and instances and usage can be monitored through the nOps _Commitment Management_ dashboard.

This article explains:

1.  [Why Use Reserved Instances.](#why-use-reserved-instances)
    
2.  [Accessing the Reserved Instance Pages via the Commitment Management Dashboard](#accessing-the-reserved-instance-pages-via-the-commitment-management-dashboard)
    
3.  [Reserved Instance Planning](#reserved-instance-planning)
    
4.  [Reserved Instance Coverage](#reserved-instance-coverage)
    
5.  [Savings Plans Recommendations](#savings-plans-recommendations)
    
6.  [Savings Plans Utilization](#savings-plans-utilization)
    
7.  [Troubleshooting](#troubleshooting-for-reserved-instance-usage)
    

## Why Use Reserved Instances ##
==========================

AWS Reserved Instances can save you significant costs compared with on-demand instance use. **Standard** reserved instances that you purchase must match certain attributes of your running instances in order to achieve the savings, such as instance type and region. **Convertible** reserved instances provide more flexibility, and **scheduled** reserved instances ensure capacity for specific time periods.

See the AWS [Types of Reserved Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/reserved-instances-types.html) documentation for a complete description of each.

nOps' _Commitment Management_ pages (Reserved Instances Planning, Reserved Instance Coverage) provide insight into your current utilization of reserved instances that you've purchased and provide planning insights to get even more cost savings from this important AWS feature.

## Accessing the Reserved Instance Pages via the Commitment Management Dashboard ##
=============================================================================

To access **Reserved Instances** management:

1.  Log into nOps.
    
2.  From the Dashboard, click **Cost** to open the drop-down menu, and choose _Commitment Management_:
    
    ![](/tmpimg/commitment-main-menu.png)
    
3.  Note that the in the Commitment Management dashboard the following tabs are for Reserved Instances:
    
    *   _Reserved Instance Planning_
        
    *   _Reserved Instance Coverage_
        
    

![](/tmpimg/com-manage-ri-planning.png)

## Reserved Instance Planning ##
==========================

Use the **Filters** in the left pane to see reserved-instance recommendations, and historical usage, by AWS account, instance type, and other criteria. Using filters to subset the recommendations can help target how your costs could improve for various reserved-instance recommendations.

Recommended Instance Reservations

*   Based on your current instance use, recommends how many reserved instances you should have to cover that use, and shows what the savings would be.
    

![](/tmpimg/ri-headers.png)

*   Note that the instance use is per combination of instance type, AWS region, and OS – the three left-hand columns.
    
*   If the number of records exceeds the table maximum, click the blue **Download** button to get a CSV that includes the full list of recommendations:

![](/tmpimg/Download-Button.png)

### Historical Usage ###
-----------------------------------------------

*   The historical usage table lists – by instance type, availability zone, and OS – your instance usage over the past five months, to aid your RI planning.
    

**Reserved Instance Coverage**
==============================

To use the Reserved Instance Coverage tab, you must first enable it.

### Enabling the Reserved Instance Coverage Feature ###
-----------------------------------------------

This tab to manage Reserved Instance Usage is only available for Client Member users who subscribe to this feature. It is not available for Partners, or for Partner Clients. Only Client Members can subscribe to this feature and configure their environment to enable the Reserved Instance Coverage tab.

This feature currently only shows coverage for EC2 instances.

To use this dashboard, you must configure your AWS environment using an nOps-authored CloudFormation stack from the [nops-aws-forwarder](https://github.com/nops-io/nops-aws-forwarder) project in the nOps GitHub repository. The project contains a [ReadMe](https://github.com/nops-io/nops-aws-forwarder#readme) that describes requirements and installation, and includes a button that launches the CloudFormation stack.

As noted in the ReadMe, you must configure [AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-a-trail-using-the-console-first-time.html) with an S3 bucket for CloudTrail logs before deploying the CloudFormation stack. A CloudTrail events log in your AWS account provides nOps the information needed to calculate RI utilization and EC2 instances. Note that the S3 bucket for AWS CloudTrail and the nOps-aws-forwarder should be within the same region.

### The Reserved Instance Coverage Tab ###
----------------------------------

The boxes at the top of this page summarize:

*   **Running Normalized Units**
    
*   **Reserved Normalized Units**
    
*   **Running Instance Coverage**
    

![](/tmpimg/ri-coverage.png)

**Running Normalized Units** and **Reserved Normalized Units** are explained by the [AWS documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/apply_ri.html) for the various instance families.

**Running Instance Coverage** is the percentage of running instances that are covered by a reserved instance – 100% means all normalized units within a given size are covered, and 0% means that none of the normalized units within a given size are covered.

Below the boxes, the **Reserved Instances** list gives RI coverage for AWS accounts broken out by region, tenancy, platform, and family.

**Note:** The column headings on this page include sorting by clicking on the column heading, plus filtering and column-choice options that appear and can be chosen when you hover over any column heading:

![](/tmpimg/Click-Column-Heading-to-Sort.png)

![](/tmpimg/ClickHamburger.png)

When you hover over a column heading, then click the symbol that appears, options appear for column sizing:

![](/tmpimg/Coverage-Page-Column-Options.png)

Note that filtering and column-choice options are also in the heading of the drop-down – here’s the filtering option used to show reserved-instance coverage for a specific region:

![](/tmpimg/Filter-by-Region-Example.png)

The column-choice options let you include in the table only the columns of use to you:

![](/tmpimg/Column-Heading-Drop-Down-Choose-Columns.png)

Symbols in the column headings show the sorting and filtering that are in effect:

![](/tmpimg/Filtered-by-Region-Sorted-by-Family.png)

Note also the arrow → in the **Action** column, which you can click to view the details page for that account group. More than one account can be included in a group.

The filtering and sorting options you’ve chosen on the main Coverage page persist on that page if you navigate to a details page then back again, and the same options are available on the details page (though the details sorting and filtering resets when you leave that page).

Note also the Refresh data button at the upper right:

![](/tmpimg/Refresh-Data-Button.png)

**Reserved Instance Coverage Details**
--------------------------------------

In the details page, accessed by clicking the arrow in the **Action** column, boxes at the top summarize account, region, OS (platform), etc. of the line you’ve chosen:

![](/tmpimg/Reserved-Instances-Details-Page.png)

The **Usage Summary** graph shows running and reserved instances in normalized units, over the last 12 hours – though you can change the time period by pulling down the blue button at the right:

![](/tmpimg/Last-12-Hours-Button.png)

![](/tmpimg/Last-12-Hours-Pull-Down.png)

The delta between the Reserved and Running lines in the graph help you understand how much under-provisioned or over-provisioned you are in reserved instances over time.

**Important:** You can set a webhook to inform you if you are running a deficit or a surplus on Reserved Instance coverage. See the [Webhooks](webhook-integrations.html) topic for more information.

Note the two tabs below the chart that provide tabulated details for reserved and running instances:

![](/tmpimg/Reserved-Instances-Details-Running-Instances-Details-Cropped.png)

And, in the tables under those tabs, the column heads provide the same sorting, filtering, and column-choice abilities as described above for the Coverage page itself. Click on any column heading to sort (repeated clicks change sort order), or hover over any column heading and click the icon that appears to filter, choose columns, and adjust column width.

Use the **Go Back** button at the upper left to return to the **Reserved Instance Coverage** page:



## Savings Plans Recommendations ##
=============================

In the **Savings Plans Recommendations** tab, you can tweak the filter properties to calculate the savings you can get on Reserved instances if you buy Savings Plans:

![](/tmpimg/2022-11-21_02-15-23.png)

In the **Filters** section, you can select the desired:

*   AWS Account
    
*   Savings Plans Type
    
    *   Compute
        
    *   EC2 Instance
        
    *   SageMaker
        
    
*   Savings Plans Term
    
    *   1 Year
        
    *   3 Year
        
    
*   Payment Option
    
    *   No Upfront
        
    *   Partial Upfront
        
    *   All Upfront
        
    
*   Look-Back Period in Days
    
    *   7 Days
        
    *   30 Days
        
    *   60 Days
        
    

Once you set the filter, in the **Recommendations** section, you can see the:

*   Upfront Cost on the Savings Plan
    
*   Hourly Commitment To Purchase
    
*   Estimated Utilization of the plan based on your current usage
    
*   Estimated Monthly Savings:
    

You will also get the look-back analysis, you can adjust the look-back period in the **Filters** section. In the **Look-Back Analysis** section, you can see:

*   Look-Back on Demand
    
*   Estimated Savings Plan
    
*   Estimated New On Demand
    
*   Estimated Savings
    
*   Estimated Return on Investment (ROI)
    
*   Minimum Hourly Charges
    
*   Maximum Hourly Charges
    
*   Average Hourly Charges
    

All the Savings Plans and the details that you see on this page come directly from AWS. When you set a filter, nOps sends your selections to AWS and simply shows the response allowing you an easy way to find the Savings Plans according to your requirements.

## Savings Plans Utilization ##
=========================

If you have purchased Savings Plans, you can see well you are utilizing the Savings Plans.

In the **Savings Plan Utilization** tab, you can select the AWS account in the Project drop-down list and use the Calendar field to filter the timeframe for which you want to check the utilization of your Savings Plans:

![](/tmpimg/2022-11-21_02-21-44.png)

In the Savings Plan Utilization tab, you can see the:

*   Net Savings For Selected Period
    
*   Savings Plans ARN
    
*   Hourly Commitment
    
*   Total Commitment (in hours)
    
*   Used Commitment
    
*   Unused Commitment
    
*   Utilization in percentage
    
*   Net Savings
    
*   On Demand Cost Equivalent
    

You can also click on the **">" icon** to see the detailed breakdown of each of your savings plan. When you click the **">"** icon, you will see:

*   Account ID
    
*   Start Date
    
*   End Date
    
*   Savings Plan Type
    
*   Instance Family
    
*   Region
    
*   Payment Option
    
*   Term
    
*   Amortized Monthly Recurring
    
*   Amortized Upfront
    
*   Amortized Total
    

**Troubleshooting for Reserved Instance Usage**
===============================================

Q: Why don't I see any data on the page?

A: There are few possibilities for why you may not see any data on this page.

*   You may have opted not to enable this feature, or you may not be using any reserved instances.
    
*   You may not have configured CloudTrail or the nOps Forwarder that provides the data to nOps. See _Enabling the Reserved Instance Coverage Feature_ above.
    
*   If you have enabled this feature and done the configuration, it may take up to 10 hours to receive data about your instances. Contact nOps Customer Support if you do not begin to see the data after that time.
    
*   This tab is not available for Partner Users or Partner Client Users