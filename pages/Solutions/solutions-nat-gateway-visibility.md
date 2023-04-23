---
title: NAT Gateway Visibility
keywords: savings, recommendations, solutions
tags: [savings, recommendations, solutions]
sidebar: mydoc_sidebar
permalink: solutions-nat-gateway-visibility.html
folder: Solutions
---

NAT Gateway, as necessary as it is to a cloud infrastructure, is also a major point of concern when it comes to costs. One little misconfiguration in a routing table can cost thousands of dollars every single day for traffic flow that could have been virtually free. It is also a cause of concern when you are unable to determine who or what is causing a spike in traffic and cost.

nOps NAT Gateway Visibility solves this “Why is this so expensive” problem that customers face. It allows you to determine the source and destination of the NAT traffic. It also provides a breakdown of flow direction, cost, and data (in Gigabytes) of each network interface instance in a given time period:

![](/tmpimg/resource-detail-cost-hist.png)

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

NAT Gateway Visibility features utilizes the VPC Flow log record published in the S3 bucket in [Parquet](https://www.databricks.com/glossary/what-is-parquet#:~:text=What%20is%20Parquet%3F,handle%20complex%20data%20in%20bulk.) format.  See [NAT Gateway Flowlogs](#getting-started-with-nat-gateway-visibility) for more information.

In order to get the insights from NAT Gateway Visibility:

1.  From the nOps **Dashboard,** go to **Cost > Cloud Resources Cost**.
    
    ![](/tmpimg/crc-menu.png)
    
2.  In the **Cloud Resources Cost** panel, go to the **Resources** tab.
    
    ![](/tmpimg/crc-resources-menu.png)
    
3.  From the resource list, click on a NAT Gateway resource to open the **Resource Details** panel.
    
    ![](/tmpimg/top-spend-resources.png)
    
4.  In the Resource Details panel, switch to the Cost History to see the details of NAT Gateway Visibility.
    
    ![](/tmpimg/nat-resource-costs.png)
    

Resource Spend History
----------------------

You can learn about your traffic trends with the help of Resource Spend History chart which breaks down the spending based on timestamps.

You can also filter the Resource Spend History based on Usage Types, Operations, Top X, and a timeframe:

![](/tmpimg/spend-operations.png)

You can also unchecking the resources for which you do not wish to see the history:

![](/tmpimg/spend-deselect.png)

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

```   

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
```

Troubleshooting Tips
====================

* If you don’t see any data in the NAT Gateway Visibility feature then check if there are any spaces in the name of the flow log file. **Make sure that there are no spaces in the name of the flow log file** that create and publish to S3.
    
* If you still don’t see any data in the feature then **give it a little time to update**. It will take a little time for the data in the NAT Gateway Visibility feature to update the first time a flow log file is created.