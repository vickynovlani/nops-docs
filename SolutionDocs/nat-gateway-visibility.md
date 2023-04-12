---
title: NAT Gateway Visibility
layout: default
nav_order: 3
has_children: false
parent: Solutions
---

NAT Gateway, as necessary as it is to a cloud infrastructure, is also a major point of concern when it comes to costs. One little misconfiguration in a routing table can cost thousands of dollars every single day for traffic flow that could have been virtually free. It is also a cause of concern when you are unable to determine who or what is causing a spike in traffic and cost.

nOps NAT Gateway Visibility solves this “Why is this so expensive” problem that customers face. It allows you to determine the source and destination of the NAT traffic. It also provides a breakdown of flow direction, cost, and data (in Gigabytes) of each network interface instance in a given time period:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/566003761/aa73714d89d7b80228f1c2de/PIZ2R8vpycjIx_Di7jWULPI2F39VT779y8Gk_225aZz82RlzgZ6HgxzRt4GCrDrdPdrmBg4bZD7C6DGefeGYV5D-WFJWzPlkergedy3QLyqOoq4_GR1O-7WVydN-gnwEP6vXwt09o1qboG-QYFeAzC8)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/566003761/aa73714d89d7b80228f1c2de/PIZ2R8vpycjIx_Di7jWULPI2F39VT779y8Gk_225aZz82RlzgZ6HgxzRt4GCrDrdPdrmBg4bZD7C6DGefeGYV5D-WFJWzPlkergedy3QLyqOoq4_GR1O-7WVydN-gnwEP6vXwt09o1qboG-QYFeAzC8)

Value of NAT Gateway Visibility
===============================

At its core, NAT Gateway Visibility allows nOps customers to identify where and from whom the increase in cost is coming from. A few major value points of this feature are given below.

PinPoint the Cause of Cost Increase
-----------------------------------

Identify the source address, destination address, and the exact network interface ID that is causing an unexpected increase in cost.

Locate Misconfigurations in Routing Tables
------------------------------------------

Staying within the Amazon network is free, i.e., traffic going through a private subnet to S3 Gateway is free. But with bad configuration all this traffic might be going through the NAT causing an unprecedented increase in costs.

Network traffic in a VPC going through the NAT to talk to another box inside the same VPC, this is a bad configuration 100% extra cost. Higher costs can also be a result of subnets talking to internal subnets using the NAT Gateway when there was no need to, costing 100% more than it should. nOps NAT Gateway Visibility offers you an easy method to locate all such misconfigurations.

Find the Top Perpetrators of Cost Increase
------------------------------------------

Use the NAT Gateway Visibility feature to quickly find out the top perpetrators of the cost increase. You have the option to filter the perpetrator based on the cost (top 50, top 75, and top 100) within a time period (1 week, 2 week, MTD, 3 months, and 6 months).

Substitute NAT Gateway with VPC Endpoints
-----------------------------------------

With the help of the source address, destination address, source AWS service, and destination AWS service against each network interface ID, NAT Gateway Visibility allows you to pinpoint the traffic that can be rerouted via VPC endpoints instead of NAT Gateway.

Learn about your Traffic Trends
-------------------------------

You can learn about your traffic trends with the help of Resource Spend History chart which breaks down the spending based on timestamps.

Traffic Flow Direction and Resulting Cost
-----------------------------------------

Increase in cost is not always the result of bad configuration, sometimes you just need to know the IPs with the most traffic resulting in an increase in overall cost.

For such cases, the nOps NAT Gateway Visibility feature also provides you the ability to see which IPs are communicating, to whom they are communicating with, and what is the cost of this communication. It also shows you the flow direction, ingress or egress.

Navigate the NAT Gateway Visibility in nOps
===========================================

NAT Gateway Visibility features utilizes the VPC Flow log record published in the S3 bucket in [Parquet](https://www.databricks.com/glossary/what-is-parquet#:~:text=What%20is%20Parquet%3F,handle%20complex%20data%20in%20bulk.) format, see the [Getting Started](https://docs.google.com/document/d/14FxQgJzi2e7PJvjdqx_OmiqomCSku3y7bh9iKAsTKdY/edit#heading=h.2k8khuujpnau) section for more details.

In order to get the insights from NAT Gateway Visibility:

1.  From the nOps **Dashboard,** go to **Cost > Cloud Resources Cost**.
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/566003765/a8d908e9380afc0180026672/OrqngC5ic2By7hVus91UfBVHM35x-yvpFgEuXY6oYMDk5L7X4JcpphXE1hvLNcrwQjmLoJ8uGVK3luyPBeiZ0h6zvNofM1dCMXp0vp4UKmusRcXXCOIVvreKR5haprVT02BEKbdFXBSrPvr7A_kixW8)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/566003765/a8d908e9380afc0180026672/OrqngC5ic2By7hVus91UfBVHM35x-yvpFgEuXY6oYMDk5L7X4JcpphXE1hvLNcrwQjmLoJ8uGVK3luyPBeiZ0h6zvNofM1dCMXp0vp4UKmusRcXXCOIVvreKR5haprVT02BEKbdFXBSrPvr7A_kixW8)
    
2.  In the **Cloud Resources Cost** panel, go to the **Resources** tab.
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/566003770/88f93f76c13e53dfd2368d21/5YowbwCQ6eWhXolRgGDB5kdfZHiTHSr4l-Wd_FSol2QHjY5ffaVbcdpR6vJ58Ojz5FsCjn7Azg7-dbiIvRMEwp0hiVaTNJX_l_URp7eCYPHjXYjBBsqKGe6SAzkPIgW133sUTh-58WnUNptZXyskKDE)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/566003770/88f93f76c13e53dfd2368d21/5YowbwCQ6eWhXolRgGDB5kdfZHiTHSr4l-Wd_FSol2QHjY5ffaVbcdpR6vJ58Ojz5FsCjn7Azg7-dbiIvRMEwp0hiVaTNJX_l_URp7eCYPHjXYjBBsqKGe6SAzkPIgW133sUTh-58WnUNptZXyskKDE)
    
3.  From the resource list, click on a NAT Gateway resource to open the **Resource Details** panel.
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/566003775/926f1f410fadffcb14c1b7cf/73aBfy8rNJ9ZPQZerVY-lO7NrdLn4XUVUdd86ScC-k72EgYpm2Dy0pGUDNN4vCk7QHwrZ8K0O4Zv_GnmTCrmxsZvSPa99cdq9kX_OntN_zMSUSKhMiUdIjp5id6agdRMzI82TUx_ECAXM8MfuyreDrM)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/566003775/926f1f410fadffcb14c1b7cf/73aBfy8rNJ9ZPQZerVY-lO7NrdLn4XUVUdd86ScC-k72EgYpm2Dy0pGUDNN4vCk7QHwrZ8K0O4Zv_GnmTCrmxsZvSPa99cdq9kX_OntN_zMSUSKhMiUdIjp5id6agdRMzI82TUx_ECAXM8MfuyreDrM)
    
4.  In the Resource Details panel, switch to the Cost History to see the details of NAT Gateway Visibility.
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/566003781/b5b0cb1cfc427939f132ac79/6XICYnZQsDaihJBgLxqJ1mjRU8NTMt1jkq9ux7ZnOfEyQtP68HWQrDjJazIlCgG6s0mWu8BvyyEEL05au0IyB9NdMoEXokP_tl8DHlqoZEfbu4Y_aje-jxUG7Zlf9HP14bpUtHtixfM3jkrnPXgRqY8)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/566003781/b5b0cb1cfc427939f132ac79/6XICYnZQsDaihJBgLxqJ1mjRU8NTMt1jkq9ux7ZnOfEyQtP68HWQrDjJazIlCgG6s0mWu8BvyyEEL05au0IyB9NdMoEXokP_tl8DHlqoZEfbu4Y_aje-jxUG7Zlf9HP14bpUtHtixfM3jkrnPXgRqY8)
    

Resource Spend History
----------------------

You can learn about your traffic trends with the help of Resource Spend History chart which breaks down the spending based on timestamps.

You can also filter the Resource Spend History based on Usage Types, Operations, Top X, and a timeframe:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/566003786/f7016c9763614b38d71074da/o2WSWYbCjyDIquCXajpOMak2uO3eD7uIDVXOqc5IK0xEa84ZDlwV1DyMN1166gZaDjIOqnxlRQna1-XfFznTaOYpmIsPsZa7qNK13vrx0PouI0RoppJ16OHkFJE0MJBNcNLmAeDmhrwYdogs6Em9n1o)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/566003786/f7016c9763614b38d71074da/o2WSWYbCjyDIquCXajpOMak2uO3eD7uIDVXOqc5IK0xEa84ZDlwV1DyMN1166gZaDjIOqnxlRQna1-XfFznTaOYpmIsPsZa7qNK13vrx0PouI0RoppJ16OHkFJE0MJBNcNLmAeDmhrwYdogs6Em9n1o)

You can also unchecking the resources for which you do not wish to see the history:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/566003790/571db998624bbe93da4f9df4/9svNshf2hcusV7HAhLnbl72y4D0guyfYJclLkCcfT3p6VSKum43lZIrRYYT-BMpiD_GRT4m5oeQL7-tlo0PyHc71_Rbh2nspQU7BmsuFVeig1hiwsWtJIEFBAQx0SlX-YOnoqMFtf0DYu9_g530f4w8)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/566003790/571db998624bbe93da4f9df4/9svNshf2hcusV7HAhLnbl72y4D0guyfYJclLkCcfT3p6VSKum43lZIrRYYT-BMpiD_GRT4m5oeQL7-tlo0PyHc71_Rbh2nspQU7BmsuFVeig1hiwsWtJIEFBAQx0SlX-YOnoqMFtf0DYu9_g530f4w8)

Network Interface Flow Logs
---------------------------

The logs available in this section are updated every 10 minutes and are aggregated by day.

Network Interface ID, Flow Direction, Source Address, Destination Address are all the fields that allow you to find out the path of the network traffic.

The source IPs belong to the NAT Gateways and the destination IPs belong to a location on the internet.

Getting Started with NAT GateWay Visibility
===========================================

To get started with the NAT Gateway Visibility feature you need to:

* [Create a flow log that publishes to Amazon S3](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs-s3.html#flow-logs-s3-create-flow-log).
    
* [Configure the flow](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs-s3.html#configure-flow-log) log to provide nOps the required fields using the [Paraquet](https://www.databricks.com/glossary/what-is-parquet#:~:text=What%20is%20Parquet%3F,handle%20complex%20data%20in%20bulk.) log format.
    

Note: To learn more about how you can log IP traffic using flow logs, see [Flow Logs](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html).

nOps Required Flow Log Fields
-----------------------------

nOps requires the following flow log configuration:

* **traffic_type:** “ACCEPTED”
    
* **log_format:**
    
    * bytes
        
    * dstaddr
        
    * end
        
    * flow-direction
        
    * pkt-dst-aws-service
        
    * pkt-dstaddr
        
    * pkt-src-aws-service
        
    * pkt-srcaddr
        
    * srcaddr
        
    

module "s3\_nops\_prod\_vpc\_flow\_logs\_bucket" {  
  source = "./logging-s3-bucket"  
  
  bucket_prefix = "${local.config.identifier}-"  
  tags          = local.config.tags  
  aws\_org\_id    = local.config.aws\_org\_id  
}  
  
resource "aws\_flow\_log" "default" {  
  log\_destination      = module.s3\_nops\_prod\_vpc\_flow\_logs\_bucket.bucket\_arn  
  log\_destination\_type = "s3"  
  traffic_type         = "ACCEPTED"  
  vpc\_id               = data.terraform\_remote\_state.vpc.outputs.vpc\_id  
  log_format           = "$${bytes} $${dstaddr} $${end} $${flow-direction} $${pkt-dst-aws-service} $${pkt-dstaddr} $${pkt-src-aws-service} $${pkt-srcaddr} $${srcaddr}"  
  tags                 = merge(  
        local.config.tags,  
        {  
          Name = local.config.identifier  
        },  
      )  
}

Troubleshooting Tips
====================

* If you don’t see any data in the NAT Gateway Visibility feature then check if there are any spaces in the name of the flow log file. **Make sure that there are no spaces in the name of the flow log file** that create and publish to S3.
    
* If you still don’t see any data in the feature then **give it a little time to update**. It will take a little time for the data in the NAT Gateway Visibility feature to update the first time a flow log file is created.