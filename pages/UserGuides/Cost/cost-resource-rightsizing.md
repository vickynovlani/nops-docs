---
title: Resource Rightsizing
keywords: cost reporting, cost history, cost allocation
tags: [cost_visibility, reporting, savings]
sidebar: mydoc_sidebar
permalink: cost-resource-rightsizing.html
folder: UserGuides
---

# Resource Rightsizing - Downsize Over Resourced EC2 Instances #


## How to use Resource Rightsizing ##
===============================

Rightsizing is one of the best ways to bring cloud costs under control. To do this you must continuously analyze instance performance, usage patterns and needs. After that, turn off idle instances and rightsize any instance that is either poorly matched to the workloads or over-provisioned.

Rightsizing is an ongoing process since resource needs are constantly changing. To achieve cost optimization make rightsizing a regular part of your cloud management process. nOps simplifies both resource analysis and monitoring.

Review Amazon Cloudwatch metrics to identify usage patterns and needs that enable you to take advantage of rightsizing opportunities:

*   **Steady State**: In the steady state, the load remains at a constant level for some time. It is even possible to forecast the compute load at any one time. For this type of usage pattern, consider Reserved Instances. They can yield significant savings.
    
*   **Variable and predictable**: For such instances, the load varies over time but on a predictable schedule. AWS Auto Scaling is ideal for applications that exhibit stable demand patterns weekly, daily, or on hourly usage variability. You can use AWS Auto Scaling to scale EC2 capacity whenever there is a spike or fluctuation in traffic.
    
*   **Dev/test/production**: Turn off production, testing, and development environments in the evening since organizations usually use them during business hours.
    
*   **Temporary:** Do you have temporary workloads with flexible starting times that you can interrupt? Avoid using an on-demand instance. Instead, place a bid on an Amazon EC2 Spot Instance.
    

Click on **Cost**


Select **Resource Rightsizing:**

![](/tmpimg/righsizingmenu.png)


Use the tabs at the top to switch between EC2, RDS, and S3:

![](/tmpimg/rightsizing-tabs.png)

Use the Filters section to look through specific information on:

*   AWS Account
    
*   Instance Types
    
*   CloudFormation: StackName
    
*   Autoscaling Group
    
*   Regions
    
*   Tags
    

**Current Config** and **Suggested Config** columns use data over the past 2 weeks to make the suggestion of downsizing:

![](/tmpimg/rightsize-suggestions.png)

Click on **Resource Details** to look at Resource Details, Cost History, and Configuration History:

![](/tmpimg/rightsizing-select-resource-details.png)

![](/tmpimg/rightsizing-ec2-metrics.png)

## How does nOps Rightsizing Algorithm Work? ##
=========================================

**With CloudWatch Enabled**

nOps collects 6 key metrics for every CloudWatch enabled EC2 instance in your environment:

*   _NetworkIn_
    
*   _NetworkOut_
    
*   _DiskReadOps_
    
*   _DiskWriteOps_
    
*   _CPUUtilization_
    
*   _mem\_used\_percent_
    

For each instance in your environment, we make the following calculations:

*   Network average
    
*   Harmonic mean of disk read and write
    
*   Disk read and write averages
    
*   Average network in / out utilization to six points of precision
    
*   Average memory utilization
    
*   Average CPU utilization
    

We continuously monitor a 30 day sample of your utilization data and match your CPU requirements to the latest offerings in the AWS pricing catalog to select the best match for your resource requirements.

**Without CloudWatch Enabled:**

nOps will recommend the latest offering upgrades for your given instance class, when they are available.