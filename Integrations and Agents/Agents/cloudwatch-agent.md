---
title: Cloudwatch Agent
parent: Agents
grand_parent: Integrations and Agents
nav_order: 3
layout: default
---

The Cloudwatch agent will run in your EC2 instances to collect metrics and send them to nOps.

This topic describes how to install Amazon CloudWatch for your AWS EC2 instances, EC2 instances that are EKS worker nodes, and then how to view the Memory Metrics through the nOps application.

1. TOC
{:toc}
    

Install Amazon CloudWatch on EC2 Instances
==========================================

To utilize the Resource Rightsizing tool to collect metrics for memory instances, install the Amazon CloudWatch agent.

nOps checks the average memory utilization for an Amazon EC2 instance over a two-week period and recommends an instance size that has at least the average memory utilization available. For example: If the current instance type has 8GB of memory available, and the average memory utilization is 700MB over a two-week period, the rightsizing recommendation will suggest an instance type that has 1GB of available memory.

**How to install Amazon CloudWatch:**

1.  [Log in to the instance using SSH](https://docs.bitnami.com/aws/faq/get-started/connect-ssh/).
    
2.  Run the following commands at the console to download and install the Amazon CloudWatch agent:
    
    wget https://s3.amazonaws.com/amazoncloudwatch-agent/debian/amd64/latest/amazon-cloudwatch-agent.deb sudo dpkg -i -E ./amazon-cloudwatch-agent.deb
    
3.  Download and install the _collectd_ daemon:
    
    sudo apt-get update && sudo apt-get install collectd
    
4.  Create the Amazon CloudWatch configuration file by running the Amazon CloudWatch configuration wizard:
    
    sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard
    
5.  [Log in to the AWS IAM console](https://console.aws.amazon.com/iam) and select the “Roles” menu item. Click the “Create role” button.  
    
    [![](https://downloads.intercomcdn.com/i/o/508477549/82ba9779a0ab648e61b57825/image.png)](https://downloads.intercomcdn.com/i/o/508477549/82ba9779a0ab648e61b57825/image.png)
    
6.  On the “Select type of trusted entity” page, select “EC2” as the service to be associated with the new role. Click the “Next: Permissions” button to proceed.
    
    [![](https://downloads.intercomcdn.com/i/o/508475263/72dd946effc92bbf4c73ffa1/image.png)](https://downloads.intercomcdn.com/i/o/508475263/72dd946effc92bbf4c73ffa1/image.png)
    
7.  On the “Attach permissions policies” page, select the “CloudWatchAgentServerPolicy”. Click “Next: Tags” to proceed.
    
    [![](https://downloads.intercomcdn.com/i/o/305154435/0132d0e2c484490bc8f70ee3/image.png?expires=1619793731&signature=5d982f8b76173b20eb4ccc29f6d1a598a9faf6c439d5612a525222caafcfffbf)](https://downloads.intercomcdn.com/i/o/305154435/0132d0e2c484490bc8f70ee3/image.png?expires=1619793731&signature=5d982f8b76173b20eb4ccc29f6d1a598a9faf6c439d5612a525222caafcfffbf)
    
8.  On the “Add tags” page, add tags if required (optional). Click “Next: Review” to proceed.
    
9.  On the “Review” page, enter a name for the new role. Click “Create role” to proceed and create the new role.
    
    [![](https://downloads.intercomcdn.com/i/o/508474711/d2b1d1a0fb4f9ee8c0bfe222/image.png)](https://downloads.intercomcdn.com/i/o/508474711/d2b1d1a0fb4f9ee8c0bfe222/image.png)
    
10. Once the role is created, click your username in the top right corner of the navigation bar and select “My Security Credentials” from the drop-down menu.
    
11. On the “My security credentials” page, click the “Create access key” button.
    
    [![](https://downloads.intercomcdn.com/i/o/305155071/a42a346eb6855c918b900a9c/image.png?expires=1619793731&signature=a79de53bbe9b805e2d53960be7e78a48c64b911585313032cf416d0d369511c5)](https://downloads.intercomcdn.com/i/o/305155071/a42a346eb6855c918b900a9c/image.png?expires=1619793731&signature=a79de53bbe9b805e2d53960be7e78a48c64b911585313032cf416d0d369511c5)
    
12. Note the new AWS access key ID and corresponding secret access key. You may want to save this to a file.  
    
13. Create an AWS credentials file with the AWS access key ID and shared access key at _/home/bitnami/.aws/credentials_ with the following content. Replace the AWS-ACCESS-KEY-ID and AWS-SECRET-ACCESS-KEY placeholders with the keys obtained in the previous step:
    
    \[default\] aws\_access\_key\_id=AWS-ACCESS-KEY-ID aws\_secret\_access\_key=AWS-SECRET-ACCESS-KEY
    
14. Edit the common configuration file for the Amazon CloudWatch agent at _/opt/aws/amazon-cloudwatch-agent/etc/common-config.toml_ and specify the path to the credentials file created in the previous step.
    
    sudo vi /opt/aws/amazon-cloudwatch-agent/etc/common-config.toml
    
      
    Update the following content:
    
    \[credentials\] shared\_credential\_file = "/home/bitnami/.aws/credentials"
    
15. Start the Amazon CloudWatch agent with the following command:
    
    sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -c file:/opt/aws/amazon-cloudwatch-agent/bin/config.json -s
    
16. Check that the agent is running with the following command:
    
    sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -m ec2 -a status
    
    [![](https://downloads.intercomcdn.com/i/o/305156957/164c695764377b799f5f97d4/image.png?expires=1619793731&signature=abd898a02eeb8e2fdf49d59260e7ce8d714718226f0a18af1f3169bb8b679640)](https://downloads.intercomcdn.com/i/o/305156957/164c695764377b799f5f97d4/image.png?expires=1619793731&signature=abd898a02eeb8e2fdf49d59260e7ce8d714718226f0a18af1f3169bb8b679640)
    

The steps described above will also configure the Amazon CloudWatch agent to automatically start on server reboot.

Learn more through the AWS Help Article: [Installing the CloudWatch Agent](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/install-CloudWatch-Agent-on-EC2-Instance.html).

CloudWatch for EKS Managed EC2 Nodes (EKS Worker Nodes)
=======================================================

You can skip this section if:

1.  You don't have any EKS worker nodes.
    
2.  The EKS worker nodes are already configured correctly with CloudWatch.
    

If you do have EKS managed EC2 nodes (EKS worker nodes), then you need to install the CloudWatch agent on EKS worker nodes using preBootstrapCommands in order to read Memory and Disk score data, otherwise the only information that will be available to you nOps will be CPU usage.

If the CloudWatch agent is not installed for EKS worker nodes, or is configured incorrectly, CloudWatch will not report any metrics for such worker nodes. If this happens, the nOps Rightsizing Recommendations will not be able to take into account the metrics that are only available through CloudWatch.

There is different set of instructions for configuring CloudWatch for EKS managed EC2 nodes (EKS worker nodes) compared to vanilla EC2 instances.

To learn how to configure/install CloudWatch agent for EKS worker nodes, see [Install the CloudWatch agent on Amazon EKS worker nodes using preBootstrapCommands](https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/install-the-ssm-agent-and-cloudwatch-agent-on-amazon-eks-worker-nodes-using-prebootstrapcommands.html).

Follow the instructions in the AWS documentation provided in the link above. It will enable CloudWatch to log the data correctly. Only then nOps will be able to provide accurate recommendations.

How to view Memory and Usage Metrics
====================================

Once CloudWatch is installed and the nOps app begins to receive the data you will be able to view resource details including memory and usage metrics.

To view metrics and usage
-------------------------

1.  Log into the nOps application.
    
2.  From a **User Dashboard** click on the **Reports** menu and select **Cloud Inventory** from the drop-down.
    
3.  On the **Cloud Inventory** page, filter the results from the left pane by selecting AWS and search for **EC2** instances using the **Filters** options.
    
4.  Click on an instance to see details.
    
5.  The **Resource** **Details** page contains 3 tabs including **Resource Details,** **Cost History**, and **Config History**.
    
6.  The **Resource Details** tab displays an **EC2 Usage Graph** that shows usage over **1 week**, **2 weeks** and **3 months**.
    
7.  You can change the CPU Utilization drop-down to see other options including **Memory Used**.
    
    [![](https://downloads.intercomcdn.com/i/o/508512921/f5362fd5120fe77977ae2326/image.png)](https://downloads.intercomcdn.com/i/o/508512921/f5362fd5120fe77977ae2326/image.png)
    
8.  To see information about this resource on AWS, click the **View Resource on AWS Console** button. You will be required to log into the AWS console to do this.
    
    [![](https://downloads.intercomcdn.com/i/o/508514272/2f9b3d4fbc26d54df93831c7/image.png)](https://downloads.intercomcdn.com/i/o/508514272/2f9b3d4fbc26d54df93831c7/image.png)