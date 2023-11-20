---
title: EventBridge Integration for Scheduler
keywords: savings, recommendations, scheduler, essentials, nswitch, eventbridge
tags: [savings, recommendations, scheduler, nswitch]
sidebar: mydoc_sidebar
permalink: scheduler-eventbridge-setup.html
folder: Essentials
series: [Essentials, Scheduler]
weight: 1.0
---
# Configuring EventBridge for Scheduler #

## Prerequisites ##

1. You must be logged in to their nOps account. 
2. Your AWS account must be configured to your nOps account.

## What is AWS EventBridge? ##

Amazon EventBridge is a fully managed event bus service that Amazon Web Services (AWS) provides. It enables you to create event-driven applications with ease by simplifying the process of handling events from various sources, including your own applications, AWS services, and third-party Software-as-a-Service (SaaS) applications.

## Why EventBridge Integration Requires ##

1. EventBridge Integration simplifies the process for nOps to automate tasks and processes within the client's environment.
2. Automatically execute events in accordance with nOps rules.
3. Initiate automation to downsize underutilized instances.
4. Facilitate the automatic, risk-free purchase or exchange of Reserved Instances (RIs) if RI utilization is suboptimal.
5. Utilize the Resource Scheduler to seamlessly power on and off groups of different instances.


## EventBridge Setup ##

### Create an EventBridge ###

1. Within the nOps Platform, click on your login to the top right.  Then select **Organization settings** > **Integrations > Eventbridge.**

    ![](https://lh4.googleusercontent.com/gjOysBglt9i1U36bB1fcmunSG49N2ZmgDpWoP8IlkPV2sHC3M_5s-wgCom_uj3iYtVABEmoWQNG071zSgKDmhDMyhIW3uE25-A_ARnggYD8t8MAaXePul764cV_mKfRjDbKVMD31SI9a03WC1x0cpAk)

1. In the Create EventBridge modal, enter the required details, and click **Create**. 

    - Give a unique name for the EventBridge, without space (such as Account-EB)
    - Select the AWS account for which you want to configure the EventBridge. In the AWS accounts list, you will only see the accounts that have been configured for nOps.
    - Select the region you want to deploy the EventBridge into.

    ![](https://lh5.googleusercontent.com/upS3YDyAuiMjPDZkUoaC6Fa-PV89ABKPMRwz0YkfQBc9SJ3BmNx8p5JaeUxTnEBNEKOHSMTK0N1c1muhsJLlK-izPz715of7MqD1DtneqwS8MFlEIvQFK62HeXOXHirnDuaRab6sYVjGupyIx2Pmw6s)

    {%include note.html content="Please ensure your quota for EventBridge bus will allow additional incoming requests, or AWS will give a limit exceeded error while creating the Eventbridge."%}

1. Once an EventBridge has been created in nOps, there will be a drop-down to access related details (account name , configuration statuses, the Launch Stack feature, Add key in KMS stack etc).

    ![](https://lh4.googleusercontent.com/Bo9JDN77uODak_xIn3oFP-Pivdq-sYFsJRefqSRCpu3QhvAr61auOveZn5ZCiG6Vi5Pq-GtjfP1Pz8ZYYSADK0B2S6duFFmMpxHZ2WDNoYTfEHcMY6025P16bffNutI3UvYCboeet3Oo5eQqeJw25PI)

{%include note.html content="By default, the status of Scheduler and Essentials will be **_Not Connected_.**"%}

 

### Configure EventBridge for nSwitch Scheduler ###

Please ensure that you are logged into the AWS account associated with the EventBridge you are configuring in the same browser before clicking on 'Launch Stack'. Additionally, confirm that the account region matches the one specified during EventBridge creation.

1. Within nOps, navigate to Organization Settings > Integrations > EventBridge.

    - Expand the EventBridge you created.
    - Click on "Launch Stack" specifically for the Scheduler.
    - This action opens a new browser tab to AWS > CloudFormation > Stacks > Create Stack.
    - Acknowledge by checking the box, then click **Create Stack**. Your EventBridge is now set up and configured.
    
    ![](https://lh4.googleusercontent.com/_8mRAmqinbeGqRkMvWYOvgOY-MfZhaYRxp-lVco67wTM6zf3K6QfJOAeUDEqMYMlEtliKhEjtJhy-58M5C-KQR5kkHy0-u6E3NuDNEnj-KVIOCxjYR0Gdd6Pea2Cs0k1g--mIS8NGYPvU9JxuLgokLM)****

    {%include note.html content="If you have a pop-up blocker enabled in your browser please be aware that it may prevent nOps from redirecting you to your AWS account for stack creation."%}

1. Once Cloudformation has successfully completed, return to nOps and click **Refresh Status**.

    ![](https://lh6.googleusercontent.com/wU4tyhsfL8gin8kvBUstwsEK0eJKUXqb5f3Iskbzk-WOT1my7ffEjQAbpr2LSDfRq1VBRNevGnEBPGS4ywvk4WZhHu3edkLt5-yT3AWOZ-i4RuVlpcxeKzHLLgCtOwybef-OtnoMMNDRdBok_C6tuBQ)

    {%include note.html content=" Connected status indicates that the EventBridge is ready for nswitch Scheduler."%}

       

### Configure EventBridge for Essentials ###

1. Navigate to Organization Settings > Integrations > EventBridge.

    - Expand the EventBridge you created.
    - Click on "Launch Stack" specifically for the Essential.
    - This action redirects you to AWS > CloudFormation > Stacks > Create Stack.
    - Acknowledge by checking the box, and then click "Create Stack". Your EventBridge is now set up and configured.

    ![](https://lh4.googleusercontent.com/M0lfPph2zMyjlPogmBC7WeE4ANa76WqQH8GKtfGkEh4xx9QMric8-FZ8No2VLK-P1gS39fgSlWFf2qC63H4QDKiaX1sHvhIrwXoJvdRD-nro0Z3ro_GgMhgelWgXlflfvJGVs91rVGlmNCSHNTM16nI)

    {%include note.html content="Please ensure that you are logged into the AWS account associated with the EventBridge you created in the same browser before clicking on 'Launch Stack'. Additionally, confirm that the account region matches the one specified during EventBridge creation."%}

    {%include important.html content="If you have a pop-up blocker enabled in your browser please be aware that it may prevent nOps from redirecting you to your AWS account for stack creation."%}

1. Once Cloud formation is completed successfully, Return to nOps and click on Refresh status to get the updated Essential status.

    ![](https://lh3.googleusercontent.com/ujA35vxnSrB2Uh7nK4gQ_sskkci-bqyEbDYOF_TS35Gh5An2TtvYCQdYd0PjFjZp2vCE4b5toLwcE71SAs69wVFDnmytfhpImfpmzL52OOrjF2DuzmZUC9GZcXqvYs7axj5Fx-H5yl2mXg5l9xla894)

    {%include note.html content="Status connected indicates that this Eventbridge is ready for nswitch Essential now."%}

Users have the capability to create an EventBridge per AWS account. Once an EventBridge has been established for an AWS account, that specific account will no longer be selectable when making a new EventBridge.

To select that AWS account again in the Eventbridge creation user needs to remove the previous EventBridge and try again the whole process.  

In nOps, the integration with EventBridge is intricately linked with the nOps Resource Scheduler. The Resource Scheduler comprises various layers, and one of these pivotal layers involves the integration and configuration with EventBridge.


<br/><br/>

{% include custom/series_related.html %}
