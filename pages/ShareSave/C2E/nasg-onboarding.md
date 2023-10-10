---
title: Onboarding your ASG clusters to nOps
keywords: savings, recommendations, sharesave, asg
tags: [savings, recommendations, sharesave, eks, asg]
sidebar: mydoc_sidebar
permalink: nasg-onboarding.html
folder: ShareSave
---

# Onboarding your ASG clusters to nOps #


## Prerequisites: ##
1. You must be logged in to your [nOps account](https://app.nops.io/accounts/signin/). 
2. Your AWS account must be configured to your nOps account.
3. You must have an Auto Scaler cluster.


## About nASG and how it works: ##

nASG is an automation tool that leverages machine learning algorithms to minimize your ASG costs by migrating its EC2 instances to Spot.

- Whenever AWS ASG launches a new on-demand instance (for example, in response to a desired capacity change), nASG Lambda will intercept this signal and launch a Spot instance with the same settings (Network Settings, User Data, Tags, etc.). It will then attach this Spot instance to the ASG, removing the on-demand instance after the newly created Spot instance is InService.

- nASG is an ML-powered tool that reduces your AWS ASG costs by automatically migrating EC2 instances to Spot. 
- nASG Lambda is aware whenever ASG launches a new on-demand instance (such as in response to a desired capacity change). In response, it automatically launches a Spot instance with settings that mirror those of the on-demand instance, attaches it to the ASG, confirms it is in service, and removes the on-demand instance for you.



## Why nASG: ##

nASG offers multiple advantages over other solutions.

- nASG predicts the spot market by analyzing its historical data and Spot Termination CT events, enabling it to select the cheapest Spot option with a low chance of being interrupted in the near future. Allows you to benefit from Spot savings with the same reliability as on-demand. By analyzing historical data and Spot Termination events, nASG automatically selects the most cost-effective and stable option — ensuring your critical workloads remain safe from interruption.
- nASG does not require your workload to be transferred to a proprietary system, but works directly with AWS ASG.
- nASG does not typically modify the ASG settings, allowing it to be disabled at any time without interrupting existing workflows.


## Steps to Configure Your ASG Cluster ##

### Step #1: Generate API Key ###

1. Navigate to Organization Settings → API key.
2. Generate a New API Key, and save it to use later in the ASG Lambda CloudFormation stack

    ![](https://lh6.googleusercontent.com/IAsFEAET1ISPBylaG0OTq1phzzGQpZt7TsYURQTwPfslbKdfpnDooipXNdE2Y7SYdwgzFBXwKe6p7qCCym6VQoyY0TWxbyvaM_RxlYFTnq3YFIl0Gkusl76FPwZcKBrFq8dj2Qa-fvWSI5-FLIdrL8s)

{%include note.html content="you can use one key for multiple AWS accounts or stacks."%}

### Step #2: Launch ASG Lambda Stack ###

1. Navigate to Organization Settings → Integrations → ASG Lambda.
2. Select the AWS account where you want to run the ASG Lambda Stack.
3. Select Launch ASG Lambda Stack. You will be redirected to the Cloudformation stack within your AWS console.
4. Input the API key that you created in step 1.2 into the Token field.
5. Acknowledge the capabilities and create the stack.
6. After successful completion, return to the nOps platform and refresh the ASG Lambda page.
7. You should see the updated version of Lambda, with the status showing a successful connection to the configured AWS account.
     
    ![](https://lh4.googleusercontent.com/FceplIGrl0w6n3omY6rnZsmTb-bcqWWQrKBdiglQtRQKY1GzcB1BbrYEU0_XfimiFp8rkTYnidIZVDEWbMkEZVQRru2AtNCE_hbDUUGBhaHs88vXCRlY10vlJK26VZ_iSLmq9q2ewGi8Un9BbcPNtqw)

{%include note.html content="Before the ASG Lambda stack runs,
<br><br> 1. The status of the version shows N/A by default.
<br>2. Auto Update is enabled by default, allowing nASG to automtically update to the newest version of Lambda. This setting can be disabled by the user if desired."%}



### Select and configure the ASG cluster ###

1\. Navigate to the ASG Dashboard and select the ASG cluster to configure

2\. Open Configure Model. 

{%include note.html content="\- The details section of Auto Scaling Group will be prefilled.<br><br>

\- The AWS Lambda configuration section will show the version detail and current status of the Lambda Stack to confirm it is properly configured on the AWS account. <br><br>

\- You can create or choose an existing ASG template in the Spot detail section."%}

3\. Create an ASG Template.

### Create a new ASG Template ###

1. Give the ASG template a unique name
2. Choose the instance families, vCPU, and Memory that are potentially suitable for your workload. From this pool, nASG will select the most optimal choice for price and stability.
3. It is recommended to select as many instance families as possible, to provide nASG with a wider recommendations pool

    ![](https://lh3.googleusercontent.com/Xudgy760nePtwLiEnQQIh9KZjKOOCC74trVtqJ8Ds9JaF8qSSoy07bdbKvcIputTWBSg4cmeoaQZ6m5uqrjDEVRJCc0q8VuDKiSCdoCRfmywv3bCVzwAjh0dg019-7SRiKN4S0dkxKS42RMy_iLc-U8)

    {%include callout.html content="you can also clone an existing template to fetch pre-defined configurations to apply to a new template." type="info" %}

4. Set the Spot percentage and Max Spot Instances using the draggable bars. 

    **Spot percentage** defines the percentage of on-demand instances to be replaced with Spot. 

    **Max Spot Instances** defines the maximum of Spot instances to be created by nASG.

5. Once values are defined, select Configure.  

6. ASG status will now display **Configured.**

    ![](https://lh3.googleusercontent.com/m-CJA6xsyBt6HO7hLCFiTH8IhrS_J1crIiqMTfokqGH9KTBXipthPp9KOK8GU0bIiyAPlcgyWM1LLsKOeGM57M-XTFick_fJIyJtgdOyRKtN68BdfrFyju5a38cyjQbf6qgAUEzUuNDa6TZGRs5WEcA)


### What to expect after configuring ASG ###

nASG Lambda will begin  replacing on-demand instances in this ASG with Spot alternatives, either every 30 minutes or upon the launch of a new on-demand instance.



## FAQ ##

### How does nASG replace on-demand instances? ####

#### New On-Demand Instance Launch Handling ####

![](https://lh5.googleusercontent.com/dCAZl2OFacVZpUSTXMN6ZePeDX9YK9wuL8ORO-P4xgG5aewpXq-FjNgxxHmrCMxP5M81OBtqzUHtaf2Qzia5Aj2k5tDwlEo489_okBhIrLx3IY9gUM2K9v1wfCSYMmPHjUcdb0nRSgv4ymlNpiVUeQs)

1. ASG launches new on-demand instance

2. Lambda intercepts `EC2 Instance State-change Notification` event from EventBridge

3. If the created instance is not protected from termination and should be replaced, nASG performs the following steps.

   1. Copy the Launch Template / Configuration from the ASG launch template
   2. In the copied Launch Template, modify Network   Interfaces / Tags / Block Device  Mappings from the instance Launch Template / Configuration if needed
   3. Fetch recommended instance types from nOps API
   4. Request Spot Fleet with the copied Launch Template and recommended instance types
   5. Once the Spot request is fulfilled, get the Spot Instance and wait for its state to be `Running`
   6. Attach the created Spot Instance to the ASG
   7. Wait for the attached Spot Instance’s state to be `InService`
   8. Terminate the on-demand instance


### Why don’t I see some of the instance families when I create a Launch Template? ###

Instance families that are not compliant with the ASG you are attempting to configure are automatically hidden. For example, if your ASG uses instances with arm64 CPU architecture, other instance families that are x86\_64 will be filtered out from the list.

### What is Auto Update Lambda, and how does it work? ###
When Auto Update is enabled, your Lambda will be automatically updated every time a new nASG version is released, (12 p.m. UTC). When you deploy nASG Lambda with Auto Update, the stack will also contain a Cross-Account role.  

### What permissions does Auto-Update Cross-Account policy have? ###

The permissions are listed below

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