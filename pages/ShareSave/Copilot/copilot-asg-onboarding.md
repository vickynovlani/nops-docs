---
title: Onboarding your Autoscaling Groups to nOps Compute Copilot
keywords: savings, recommendations, sharesave, asg, copilot, autoscaling
tags: [savings, recommendations, sharesave, copilot, asg]
sidebar: mydoc_sidebar
permalink: copilot-asg-onboarding.html
folder: ShareSave
series: [ShareSave, Copilot, Onboarding]
weight: 1.0
---


# Introduction to Compute Copilot for Autoscaling Groups (ASG) #

## About Compute Copilot for ASG and how it works ##


- Compute Copilot is a service that automatically optimizes any compute-based workload. It leverages ML algorithms to reduce your AWS ASG costs by automatically migrating EC2 instances to Spot. 
- Compute Copilot Lambda is aware whenever ASG launches a new on-demand instance (such as in response to a desired capacity change). In response, it automatically launches a Spot instance with settings that mirror those of the on-demand instance, attaches it to the ASG, confirms it is in service, and removes the on-demand instance for you.


## Why Compute Copilot ##

- Compute Copilot uses AI-driven decision making to provision and run auto scaling group instances at the cheapest price in real time, without manual effort.
- Compute Copilot allows you to benefit from Spot savings with the same reliability as on-demand. By analyzing historical data and Spot Termination events, it ensures your critical workloads remain safe from interruption. 
- Compute Copilot does not require your workload to be transferred to a proprietary system, but works directly with AWS ASG.
- Compute Copilot does not typically modify the ASG settings, allowing it to be disabled at any time without interrupting existing workflows.

## Prerequisites ##

1. You must be logged in to your [nOps account](https://app.nops.io/accounts/signin/). 
2. Your AWS account must be configured to your nOps account.
3. You must have the correct permissions. 

In the Compute Copilot Auto Scaling Groups Onboarding call, we will launch a CloudFormation Stack to create (1) a Lambda and its associated resources, and (2) a StackSet to create an EventBridge Forwarder in the same account but in all the SCP enabled regions of the same account.


Two primary roles are needed to create this CloudFormation Stack:

1. AWSCloudFormationStackSetAdministrationRole
2. AWSCloudFormationStackSetExecutionRole


These roles should exist in the AWS account where most of your ASGs are present, with these exact names. Before the Onboarding call, we ask that you verify that the above roles exist to ensure we can proceed successfully. 


- If these roles exist, no further action is required prior to the Onboarding call. 

- If these roles do not exist, please follow the below steps involving IAM Roles and Policy Creation:

1. In the **AWS account**, create a **Policy** with the name “AssumeRole-AWSCloudFormationStackSetExecutionRole” as following:&#x20;


```json
{
"Version": "2012-10-17",
"Statement": [
	{
	  "Action": [
			"sts:AssumeRole"
	],
	  "Resource": [
			"arn:*:iam::*:role/AWSCloudFormationStackSetExecutionRole"
	],
	  "Effect": "Allow"
	}
  ]
}
```

2. Create a new **IAM Role** with the name “AWSCloudFormationStackSetAdministrationRole” and attach the **Policy** we created in the above step (“AssumeRole-AWSCloudFormationStackSetExecutionRole”). Once it is attached, create the **IAM Role**.
3. Navigate to the **IAM Role** we created →  **Trust Relationships** tab. Edit the trust relationship to the following:

```json 
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "cloudformation.amazonaws.com"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}
```

4. Navigate back to **IAM Roles**, and create another new **IAM Role** named “AWSCloudFormationStackSetExecutionRole.” and for the policies we will be giving “AdministratorAccess” Permission Policy and let’s go ahead and create the role \
   ![](https://lh7-us.googleusercontent.com/Q2TBm3_s2aBb4M5VEwlnA1C3qmygDP3lqAP3vaBE3lupf-Q_N2SzZ_RoSl-5AXdYZxk31VJtwZokbQbJeG3P9A2faK65PtiqPsv1rYBW6z0ifKX7nl9Ke3JUT_sI8_t4h-sFFkDDcKj227hRcVzO0XI)\
   5\. Navigate to **Trust Relationships** tab of the “AWSCloudFormationStackSetExecutionRole” and edit the trust relationship to the following:&#x20;

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::accountnumber:root"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}


```

In the above Principal, the account number should be that of the account you are currently logged in to.



We have now successfully created the roles and policies necessary to create StackSets in this AWS Account. 



For further reference, please refer to [AWS Documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacksets-prereqs-self-managed.html)



## Steps to Configure Your ASG Cluster ##



### Generate API Key ###
- Navigate to Organization Settings → API key.
- Generate a New API Key, and save it to use later in the ASG Lambda CloudFormation stack
    ![](https://lh7-us.googleusercontent.com/DUWPDI1CSnO5kyjylFhvv0hzlluqiRjkz6vWk-1lT6_xhsgReVNxdFxNTd2j2hmaYeiXUE3uz4mQVl5GKA_MakQuTMfMIBdPALiP4tWhSC5qLhLsYKCpE70RaeOat6t6FKENiNkVs0eQNKO6TYkZzaQ)

    **_Note: you can use one key for multiple AWS accounts or stacks._**



### Launch ASG Lambda Stack in the AWS Account ###
1. In the nOps dashboard, Navigate to **Organization Settings** → **Integrations** → **ASG Lambda**.
- Select the AWS account where you want to run the ASG Lambda Stack.
- Select **Launch ASG Lambda Stack**. You will be redirected to the Cloud formation stack in the AWS console.
- Input the API key that you created in step 1.2 into the Token field.
- Acknowledge the capabilities and create the stack.
- Please verify in your AWS account that you are able to see the following StackSet and stack that was created via Terraform.
    ![](https://lh7-us.googleusercontent.com/gYsBQgyqah3mLZA3s288f9x1UrpoJ9bF4dbswlfMlCH1IEMWvExs4YEndnlGUYGvCfPEozQii1Umw0FSwirGd7TlRh6k7dGsYeZI3ASlK4HaZ7h_KjSCOp3UXiinqI0-bHrB6HRUZ2p1zVq01704g58)
        
    _Under Stacks, you should be able to see the above in Stack instances in the same region as stacks._
    ![](https://lh7-us.googleusercontent.com/lwMnfBrpJZR_blrNdWoHK9NMkDguDxq1RElS80U5SUBxYRgWf26O6761sBvVdTGBZZUfUd86hOEXPI5boVZ8lYAQqQIPn18A7H7xl0wIPRvmOJmMx-SVJacikpb5__EM4EA4KVB_HteL6oHLsCbJX-c)\
    Notes: _Under StackSets, you should be able to see the above in Stackset in the same region as stacks. Please verify the status._ _You might see the stackset creating a stack only in few regions instead of all regions and this is not of concern as stackset fails to create a stack in other regions due to SCP’s_

1. After successful completion, return to the nOps platform and refresh the ASG Lambda page.
1. You should see the updated version of Lambda, with the status showing a successful connection to the configured AWS account.

    ![](https://lh7-us.googleusercontent.com/4-Ufml5d-uWKQskNwDKrWxQgQ0wUF6PSm66Hb1kUv3WsfkuLyfDeC9VLKxFHQbQJkobMVTDrUElM_Q3P4GMMMUCf9LBHMq2D3PIPEFsH8Wva-yY1E2SNcKs6fDhF5mmdq7kgBA3NIcV_uat7hcD5ptw)
    
    Note: Before the ASG Lambda stack runs,
    - The status of the version shows N/A by default.
    - Auto Update is enabled by default, allowing Compute Copilot to automatically update to the newest version of Lambda. This setting can be disabled by the user if desired.


### Select the ASG cluster and configure ###

1. Navigate to the ASG Dashboard and select the ASG cluster to configure
    - Open Configure Model. The details section of Auto Scaling Group will be prefilled. 
    - The AWS Lambda configuration section will show the version detail and current status of the Lambda Stack to confirm it is properly configured on the AWS account. 
    - You can create or choose an existing ASG template in the Spot detail section.

1. Create an ASG Template.
    - Give the ASG template a unique name
    - Choose the instance families, vCPU, and Memory suitable for your workload. From this pool, Compute Copilot will select the most optimal choice for price and stability.
    - It is recommended to select as many instance families as possible, to provide Compute Copilot with a wider recommendations pool
    ![](https://lh7-us.googleusercontent.com/dnUIMeRRJHeoELoRW9Z_3ZfCiguNzJR1FTUQFLSXCvJpjTYa1bvhaeKyygjfShvlXnCloRmAcwoXPQIyXRvrjWZKJTu8HzOMARAIVrw1qS0GyJaqHYFK9HhDujZTvvTKK84htHhQzhxyB27BE3U6sb0)
    
    _Note: you can also clone an existing template to fetch pre-defined configurations to apply to a new template._ 



1. Set the Spot percentage and Max Spot Instances using the draggable bars. 

**Spot percentage** defines the percentage of on-demand instances to be replaced with Spot. 

**Max Spot Instances** defines the maximum of Spot instances to be created by Compute Copilot.


1. Once values are defined, select Configure.  

1. ASG status will now display **Configured.**
    ![](https://lh7-us.googleusercontent.com/7HPFh5aoXx0mdrFmDFAeBq4nXfoWIfVO_ZndTglaaqGA8r6VJdoQBI2FQ6HaZQ0rIhg8N9nCJbPdMPzKCHJAW0OwgnRWJO247MegWvYd4cyLj4j3bJgEP_05QBgrv8923jvp9EgCuSil61zLNsXMv7o)


### What to expect after configuring ASG ###

Compute Copilot Lambda will begin replacing on-demand instances in this ASG with Spot alternatives, either every 30 minutes or upon the launch of a new on-demand instance.



## FAQ ##



1. **How does Compute Copilot replace on-demand instances?**
    ![](https://lh7-us.googleusercontent.com/OjZwU_zk5KM1CXUihO_evtZwp-L6bkNXBvQHzcqCdD39OkO-t_KdEcQLYKBKLYV1l8SO2GLJgB7jtaG6Rr_9gWX-FpbznWEPW1Xt7Sv9ClZX0wJW6-YhrMTHgStuHXWM43z_H0-pZsAKVHRxXNSpzsM)
    
    1. ASG launches a new on-demand instance
    1. Lambda intercepts the EC2 Instance State-change Notification event from EventBridge
    1. If the created instance is not protected from termination and should be replaced, Compute Copilot performs the following steps. 
        1. Copy the Launch Template or Launch Configuration from the ASG launch template
        2. In the copied Launch Template, modify Network Interfaces, Tags, Block Device and/or Mappings from the instance Launch Template or Configuration if needed
        3. Fetch recommended instance types from nOps API
        4. Request Spot Fleet with the copied Launch Template and recommended instance types
        5. Once the Spot request is fulfilled, get the Spot Instance and wait for it to its state to be Running
        6. Attach the created Spot Instance to the ASG
        7. Wait for the attached Spot Instance’s state to be InService
        8. Terminate the on-demand instance

2. **Why don’t I see some of the instance families when I create a Launch Template?**

    Instance families that are not compliant with the ASG you are attempting to configure are automatically hidden. For example, if your ASG uses instances with arm64 CPU architecture, other instance families that are x86\_64 will be filtered out from the list.

3. **What is Auto Update Lambda, and how does it work?** 

    When Auto Update is enabled, your Lambda will be automatically updated every time a new Compute Copilot version is released (12 p.m. UTC). When you deploy Compute Copilot Lambda with Auto Update, the stack will also contain a Cross-Account role.  


4. **What permissions does Auto-Update Cross-Account policy have?**


```yaml 

Action:
- cloudformation:CreateChangeSet
- cloudformation:DescribeStackInstance
- cloudformation:DescribeStackResources
- cloudformation:DescribeStacks
- cloudformation:GetTemplateSummary
- cloudformation:UpdateStack
Resource:
- !Ref AWS::StackId

Action:
- cloudformation:CreateChangeSet
- cloudformation:DescribeStackEvents
- cloudformation:DescribeStackInstance
- cloudformation:DescribeStackResources
- cloudformation:DescribeStacks
- cloudformation:DescribeStackSet
- cloudformation:DescribeStackSetOperation
- cloudformation:GetTemplateSummary
- cloudformation:UpdateStackInstances
- cloudformation:UpdateStackSet
Resource:
- !Sub NASGEventBridgeForwarderMultiRegion

```



{% include custom/series_related.html %}