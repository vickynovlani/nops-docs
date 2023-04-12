---
title: nOps Cost Optimization Recommendations
layout: default
nav_order: 5
has_children: false
parent: Solutions
---

nOps provides several forms of cost optimization recommendations ranging from unused, underutilized, and infrequently accessed resources to resource rightsizing recommendations.

In the nOps platform, you can find cost optimization recommendations on the:

* **Rules > Cost** tab**:**
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573878597/82bef4558ad154fcec27cbe6/PjQK2CZwnMSLgXIqUm4mAUIh_14ulOJQDrO4_bIRELGwhWQhr2ARaceJp9icfJbCY3xpQ-oUpkXKMYNaVcsct7t_PofzEaeNM041qVN0AO0CMaRwQjrm1MBHgWUXpm88gYFKImoAER4-mlBIUu5-bh4)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573878597/82bef4558ad154fcec27cbe6/PjQK2CZwnMSLgXIqUm4mAUIh_14ulOJQDrO4_bIRELGwhWQhr2ARaceJp9icfJbCY3xpQ-oUpkXKMYNaVcsct7t_PofzEaeNM041qVN0AO0CMaRwQjrm1MBHgWUXpm88gYFKImoAER4-mlBIUu5-bh4)
    
    * Unused
        
    * Underutilized
        
    * Infrequently Accessed
        
    * Rightsizing
        
    * Miscellaneous
        
    
* **Cost > Resource Rightsizing** page**:**
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573878606/e4745290dc607d52748dd506/_3xcP_0vXESh9Wze3LOX8_H2EU55-H2XYKDIALafJgGomM1ocXz1KTSCeUtgngzIZm9OEPFMnNVlAgTdDWRRH_rGR5hmcPVcR96_PGxf5tWvuRrpxrf1LweCsSkM75oEQPOCZ7cKgjcaDnfsXuRcGVk)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573878606/e4745290dc607d52748dd506/_3xcP_0vXESh9Wze3LOX8_H2EU55-H2XYKDIALafJgGomM1ocXz1KTSCeUtgngzIZm9OEPFMnNVlAgTdDWRRH_rGR5hmcPVcR96_PGxf5tWvuRrpxrf1LweCsSkM75oEQPOCZ7cKgjcaDnfsXuRcGVk)
    
    * EC2 Rightsizing
        
    * RDS Rightsizing
        
    * S3 Rightsizing

1. TOC
{:toc}   
    

nOps Rules Cost Recommendation
==============================

The cost optimization recommendations in the **Rules > Cost** tab provides cost optimization recommendations with details of the appropriate step you can take.

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573878613/a7c7c84ff78f6a9f7f6ec0e9/F0476ZQGgoU0DlymAglQarc6rVkXBuOS0VAcNL0j-Y0dgjbDFU1l0fClGafRtizszLni6pM9hA6VGmJawPfSy7XKM7BThev0f0MEBIDsqUxm-BawLGi9mADDfYKYUZ6G8cD3yDyPAW5MixKWtYTxP-8)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573878613/a7c7c84ff78f6a9f7f6ec0e9/F0476ZQGgoU0DlymAglQarc6rVkXBuOS0VAcNL0j-Y0dgjbDFU1l0fClGafRtizszLni6pM9hA6VGmJawPfSy7XKM7BThev0f0MEBIDsqUxm-BawLGi9mADDfYKYUZ6G8cD3yDyPAW5MixKWtYTxP-8)

Following is a list of cost optimization recommendations that nOps provides in the **Cost** page. The list is not exhaustive, nOps is constantly adding more recommendations that will help you reduce costs:

* **Unused:**
    
    * Unused AWS EBS Volumes
        
    * Unused AWS Elastic IP (EIP) Resources
        
    * Unused AWS NAT Resources
        
    * Unused Azure Disk Storage
        
    * Unused Azure Network Interfaces
        
    * Unused Azure Public IP Addresses
        
    * Unused Azure Virtual Machine
        
    * Unused Azure Virtual Network NAT
        
    
* **Underutilized:**
    
    * Underutilized AWS CloudWatch Log Group
        
    * Underutilized AWS EBS Provisioned IOPS
        
    * Underutilized AWS ELB Resources
        
    * Underutilized AWS RDS Provisioned IOPS
        
    * Underutilized (% read/write) CosmosDB Containers
        
    * Underutilized (% read/write) DynamoDB Tables
        
    * Underutilized (%) ECS Cluster
        
    * Underutilized (% capacity) EC2 Instances
        
    * Underutilized Azure Virtual Machine
        
    
* **Infrequently Accessed:**
    
    * Infrequently Accessed AWS S3 Bucket
        
    * Infrequently Accessed Azure Storage Account Buckets
        
    * Infrequently Accessed Azure Storage Account Resources
        
    
* **Rightsizing:**
    
    * Review EC2 Instances (low traffic)
        
    * Review EC2 Instance Size
        
    * Review S3 Storage Class
        
    * Review MySQL Instance Size
        
    * Review Azure MariaDB Instance Size
        
    * Review Azure PostgreSQL Instance Size
        
    
* **Misc:**
    
    * Disabled Autoscaling CosmosDB Containers or Databases
        
    * Disabled Autoscaling DynamoDB Tables
        
    * Unattached Workspace Directory
        
    

Resource Rightsizing Recommendations
====================================

Rightsizing is one of the best methods to bring cloud costs under control. nOps provides resource rightsizing recommendations for these AWS services:

* EC2
    
* RDS
    
* S3
    

Each service has its own dedicated tab with recommendations:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573878620/17b544787ea640abc62197c1/yx2YbipkC9aE6oXr6UnQK6LPPqzwGKL8wHNCJqxPoF8ue73UYMg4hBPTGOyearswrtC4FZaScMjcO6G1FYRGIGGBc5xQU8s-fn2NI_Wq8asNVdYiqKT3d4f3JyYAHOYlSHyMZFJKqZ9woOOT3eKu32M)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573878620/17b544787ea640abc62197c1/yx2YbipkC9aE6oXr6UnQK6LPPqzwGKL8wHNCJqxPoF8ue73UYMg4hBPTGOyearswrtC4FZaScMjcO6G1FYRGIGGBc5xQU8s-fn2NI_Wq8asNVdYiqKT3d4f3JyYAHOYlSHyMZFJKqZ9woOOT3eKu32M)

To reduce costs by rightsizing, nOps allows you to analyze instance performance, usage patterns and needs continuously. nOps then provides cost optimization recommendations to turn off idle instances and to rightsize instances that are either poorly matched to the workloads or over-provisioned.

On the **Resource Rightsizing** page, against each resource, nOps provides:

* AWS Account
    
* Region
    
* Resource Name/ID
    
* Current Configuration
    
* Suggested Configuration
    
* Unused CPU(%)
    
* Current Monthly Cost
    
* New Monthly Cost (If the _Suggested Configuration_ is implemented)
    
* Monthly Savings
    

Rightsizing is an ongoing process since resource needs are constantly changing. nOps simplifies both resource analysis and monitoring, which enables you to make rightsizing a regular part of your cloud management process.

nOps analyzes your resourse and provides cost optimization recommendations based on the state and usage of resources. nOps categorizes the resources and recommendations based on these states:

* **Steady State:** In the steady state, the load remains at a constant level for some time. It is even possible to forecast the compute load at any one time. For this type of usage pattern, consider Reserved Instances. They can yield significant savings.
    
* **Variable and predictable:** For such instances, the load varies over time but on a predictable schedule. AWS Auto Scaling is ideal for applications that exhibit stable demand patterns, weekly, daily or hourly usage variability. You can use AWS Auto Scaling to scale EC2 capacity whenever there is a spike or fluctuation in traffic.
    
* **Dev/test/production:** Turn off production, testing, and development environments in the evening since organizations usually use them during business hours.
    
* **Temporary:** Do you have temporary workloads with flexible starting times that you can interrupt? Avoid using an on-demand instance. Instead, place a bid on an Amazon EC2 Spot Instance.
    

The nOps Process
================

The recommendations of nOps are based on a rigorous process that is often unique for each form of recommendation.

Following are examples of how nOps comes to the conclusion that rightsizing is required and offers you the recommendation to act upon.

AWS EKS
-------

Let’s say you have an **AWS EKS** instances that is m6i.xlarge, nOps looks at no less than 23 different metrics and concludes the right size of the instance according to your current need:

|     |     |
| --- | --- |
| **Instance Type** | m6i.xlarge |
| **max\_cpu\_usage_max** | 1   |
| **max\_ram\_usage_bytes** | 3220504279 |
| **max\_cpu\_cores_limit** | 0   |
| **max\_ram\_bytes_limit** | 3221225472 |
| **min\_cpu\_cores_limit** | 0   |
| **min\_ram\_bytes_limit** | 0   |
| **total\_instance\_count** | 12993 |
| **total\_pod\_count** | 12993 |
| **min\_cpu\_cores\_allocated\_by_nodegroup** | 0   |
| **max\_cpu\_cores\_allocated\_by_nodegroup** | 0   |
| **min\_ram\_bytes\_allocated\_by_nodegroup** | 0   |
| **max\_ram\_bytes\_allocated\_by_nodegroup** | 3221225472 |
| **Memory** | 17179869184 |
| **vCPU** | 4   |
| **mem\_usage\_diff_bytes** | 13959364905 |
| **mem\_usage\_diff_percent** | 0.8125419789575972 |
| **cpu\_usage\_diff** | 3   |
| **cpu\_usage\_diff_percent** | 0.75 |
| **mem\_limit\_diff_bytes** | 13958643712 |
| **mem\_limit\_diff_percent** | 0.8125 |
| **cpu\_limit\_diff** | 4   |
| **cpu\_limit\_diff_percent** | 1.0 |
| **Recommendation** | Please update the instance type to m5d.2xlarge |

In this case, nOps recommends that you update your instance from **m6i.xlarge** to **m5d.2xlarge**.

AWS CloudWatch
--------------

If you have CloudWatch enabled, nOps will collect 6 key metrics for every CloudWatch enabled EC2 instance in your environment:

* NetworkIn
    
* NetworkOut
    
* DiskReadOps
    
* DiskWriteOps
    
* CPUUtilization
    
* mem\_used\_percent
    

For each instance in your environment, nOps will make the following calculations:

* Network average
    
* Harmonic mean of disk read and write
    
* Disk read and write averages
    
* Average network in / out utilization to six points of precision
    
* Average memory utilization
    
* Average CPU utilization
    

nOps continuously monitors a 30 day sample of your utilization data and matches your CPU requirements to the latest offerings in the AWS pricing catalog in order to select the best match for your resource requirements.

If you don’t have CloudWatch enabled, nOps will still recommend the latest offering upgrades for your given instance class, when they are available.