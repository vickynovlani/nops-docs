---
title: Using EventBridge with nSwitch to Reduce Costs Automatically
keywords: savings, recommendations, solutions
tags: [savings, recommendations, solutions]
sidebar: mydoc_sidebar
permalink: solutions-using-eventbridge-with-nswitch-to-reduce-costs.html
folder: Solutions
---

The nOps EventBridge integration allows our customers to act on optimization recommendations provided by our AI-driven platform. Use our simple to deploy lambdas to automatically remediate or schedule remediation for common cloud waste issues, customize events to build your own workflow, or use our scheduler app to automatically enable and disable groups of EC2 and RDS instances.

EventBridge is an easy way for doing integrations with AWS Infrastructure, and it also supports multi partner event sources.

In nOps, EventBridge integration is closely tied to the nOps Resource Scheduler. There are many layers to the Resource Scheduler, and one of those layers is the EventBridge integration and configuration.

1. TOC
{:toc}

Use Cases
=========

Automate any nOps Optimization Recommendation:

* Clean up cloud waste
    
* Schedule, stop, and start resources
    
* Terminate instances
    
* Rightsize instances
    
* Configure Reserved Instances
    

Types of Events that nOps EventBridge Publishes
===============================================

A catalog of detail types that illustrate the types of events your integration publishes. Include this information as part of your customer-facing documentation.

* Infrequently accessed S3 bucket(s)
    
* Underutilized resources
    
* Infrequently accessed EFS
    
* ECS cluster with underutilized resources
    
* S3 rightsizing recommendation
    
* EC2 instance rightsizing recommendation
    
* RDS instance rightsizing recommendation
    
* DynamoDB low utilization
    
* CloudWatch log groups underutilized resources
    
* IOPS performance check
    
* DynamoDB throughput check
    
* Unused AWS resource details
    
* EC2 slow network traffic details
    
* RDS instance idle
    
* Unattached workspace directories
    

Sample Event
============

Event payloads can be customized, but the default event format for our MVP rule set follows this pattern:
```
{

    "version": "0",

    "id": "d2949071-573b-c67a-93a5-530604aec254",

    "detail-type": "nOps notification for 'rule'",

    "source": "aws.partner/nOps.io.test/012345678912/nops_uat_notification_12345_AWSDEMOUSEAST",

    "account": "012345678912",

    "time": "2022-09-21T09:21:23Z",

    "region": "us-east-1",

    "resources": [

 

    ],

    "detail": {

        "account_number": "012345678912",

        "description": "sg-abcd1234",

        "details": {

            "_id": "78ee385ce11c818238e57663240372eb",

            "compliant": "False",

            "name": "default",

            "timestamp": 1645920000,

            "violation_date": "2022-02-27",

            "violation_type": "unrestricted_ssh"

        },

        "item_hash": "item_hash",

        "name": "unrestricted_ssh",

        "region": "us-east-1",

        "time": "2022-02-27"

    }

}
```

EventBridge Integration
=======================

EventBridge Integration makes it easier for nOps to automate workflows in the client’s environment.

Amazon EventBridge is a serverless event bus that makes it easier to build event-driven applications at scale using events generated from your applications, integrated Software-as-a-Service (SaaS) applications, and AWS services.

With EventBridge integration, nOps will be able to:

* Automate events based on nOps rules.
    
* Trigger an automation to reduce the size of underutilized EC2 instances.
    
* Purchase or exchange RI automatically risk-free, if RI utilization is not optimized. To see the nOps list of risk-free commitments, go to **ShareSave Dashboard > List of Opportunities > List of Risk-Free Commitments**.
    
* Turn on and off the EC2 and RDS instances in a group with the Resource Scheduler.
    
* Trigger messages in multiple services other than the event messages.
    

To add nOps as an EventBridge partner, go to **AWS > Amazon EventBridge >** **Partner event sources**, and select **nOps** as one of the options to listen. Click on **Setup** and configure the options:

![](/tmpimg/sol-partner-sources.png)

Once the EventBridge integration is set up, you can create event sources directly from the nOps application and deploy them to any account and region that you’ve connected to nOps.

To integrate your AWS EventBridge with nOps, log in to nOps and click **User Avatar > Organization Settings > Integrations > EventBridge**. In the _Event Bridge_ tab click **\+ Create EventBridge**:

![](/tmpimg/sol-create-eventbridge.png)

In the **Create New Event Bridge** page:

1.  Create a name for this EventBridge.
    
2.  Select the AWS account you want to deploy the EventBridge into. In the AWS accounts list, you will only see the accounts that you onboard into nOps.
    
3.  Select the region you want to deploy the EventBridge into.
    
4.  Click **Create**.
    

![](/tmpimg/sol-eventbridge-create-save.png)

When you click **Create**, nOps will deploy the EventBridge into your selected AWS account and region by creating an event bus in the selected AWS account.

To see the event bus that nOps just created, go to **AWS > Amazon EventBridge > Event buses > Custom event bus**.

The next step is to add an EventBridge target into Webhooks.

Adding EventBridge Target into nOps Webhooks
============================================

nOps has a Webhook for almost every cost optimization rule in the nOps environment.

When you create a Webhook, anytime an associated event is fired a message will be sent to either the endpoint you define or the EventBridge that you create.

To add an EventBridge target into nOps Webhooks, go to **User Avatar > Organization Settings > Integrations > Outgoing Webhooks**. In the _Outgoing Webhooks_ tab, click **\+ Create New Webhook**:

![](/tmpimg/sol-webhook001.png)

In the **Create New Webhook** page:

![](/tmpimg/new-webhook.png)

1.  Create a **name** for the Webhook.
    
2.  Select an **Event**. Notice that the Event option has two fields, in the first field you need to select the event category, and in the second you need to select the actual event.
    
3.  Select an **Endpoint**, it can be either a simple Endpoint (Target URL) or an **EventBridge**. In the scope of this documentation we are only going to select the EventBridge option. Selecting this option will send the Webhook to your EventBridge.
    
4.  Select an EventBridge from the list. The list consists of all EventBridges that you create in **nOps > Organization Settings > Integrations > EventBridge** tab.
    
5.  Click **Save**.
    

EventBridge Automatic Configuration Walkthough
==============================================

When you create an EventBridge in nOps, nOps will automatically create an event bus in your selected AWS account. To see the event bus that nOps automatically created, go to **AWS > Amazon EventBridge > Event buses > Custom event bus**.

Once, you have configured the webhook, come back to the **nOps > Organization Settings > Integrations > EventBridge** tab and click **Launch Stack** against the EventBridge that you created:

![](/tmpimg/sol-launch-stack.png)

* * *

**Note:** Before you click **Launch Stack**, make sure that you are logged into the AWS account that you used for the EventBridge. You also need to make sure that the account region is the same as the one you specified while creating the EventBridge.

* * *

When you click Launch Stack, you will be redirect to **AWS > CloudFormation > Stacks > Create stack:**

![](/tmpimg/sol-create-stack.png)

_You can follow the link highlighted above to see the CloudFormation template. To see the CloudFormation template right now, see [Scheduler CloudFormation Template](https://s3-us-west-2.amazonaws.com/nops-rules-lambda-sources/scheduler/scheduler.yml)._

Check the acknowledgement box, and click **Create stack**. The EventBridge is now ready and configured.

EventBridge Manual Configuration Walkthrough (Not Recommended)
==============================================================

This is an example of manual EventBridge configuration with AWS SQS.

Create a Target Queue in AWS - SQS
----------------------------------

First, we will create a target queue in AWS - SQS. To create a queue, go to **AWS > Amazon SQS > Queues > Create queue.** In the **Create queue** page, enter a suitable name for the queue in the **Name** field and leave all other fields as is. Click **Create queue**.

Next we will create an EventBridge.

Configure the Event Bridge in your AWS Account
----------------------------------------------

When you create an EventBridge in nOps, nOps will automatically create an event bus in your selected AWS account. To see the event bus that nOps automatically created, go to **AWS > Amazon EventBridge > Event buses > Custom event bus**.

Now, you need to create an EventBridge rule in your AWS account. To create an EventBridge rule, go to **AWS > Amazon EventBridge > Rules** and click **Create Rule**.

In the Event bus option, select the event bus that nOps created for you. The name of the event bus will be the same as the EventBridge that you created in nOps.

![](/tmpimg/sol-eb-create-rule.png)

When you click next, the next step is **Build Event Pattern**. In the **Build** **Event pattern** section, select the **Custom patterns (JSON editor).** In this example we will use the following patterns:

{

"detail-type": \[ {

"anything-but": "initializing"

} \]

}

For the full list of nOps Event Patterns, see **nOps EventBridge Event Patterns**.

Enter the **Event pattern** and click **Next**:

![](/tmpimg/sol-json-pattern.png)

The next step is **Select target(s).**

In the target list, there are a lot of targets that you can select. In the future we will also provide numerous Lambda functions. In the scope of this example, we will select the SQS queue and select the queue you created in the beginning of the walkthrough, and then click **Next**:

![](/tmpimg/sol-save-targets.png)

The next section is the **Configure tags** section, which is optional. In the scope of this example, you don’t need to add any tags, simply click **Next**:

![](/tmpimg/sol-eb-rule-tags.png)

The next section is the final section, **Review and create**. In this section review the rule and click **Create Rule**.

Send Demo Message
-----------------

In order to check if the EventBrdige was configured correctly, we will send a test message to Amazon SQS via the Webhook that we created. To send the test message , go to **nOps > Organization Settings > Integrations > Outgoing Webhooks** and click the icon highlighted below against the Webhook:

![](/tmpimg/sol-webhook002.png)

Now, to check if the message is received, go to your **AWS > Amazon SQS > Queues > \[The queue you created\]**. In the queue, click the **Send and receive messages** button:

![](/tmpimg/sol-send-receive.png)

On the **Send and receive messages** page, click the **Poll for messages** button:

![](/tmpimg/sol-poll-message.png)
If the configuration was successful, you will receive the test message in the **Messages** section.

nSwitch Recommendations
==================================

nOps identifies opportunities to turn computers, resources, instances, and databases off at certain hours. Expensive environment when not being used still costs if they are not turned off.

nOps looks at your usage statistics and makes recommendations to schedule resources for availability during a specific time frame when they are expected to be used. You can then schedule these resources to start and stop using nSwitch.

To see the nSwitch Recommendations and the potential savings that scheduling resources can provide, go to **nOps > ShareSave Dashboard > nSwitch**:

![](/tmpimg/sol-sched-section.png)

Click on an opportunity to expand it. nOps will provide you with a recommendation of schedule against each instance type and an estimate of the potential savings:

![](/tmpimg/sol-sched-shedules.png)

You can either create a schedule directly from the Resource Scheduler section by clicking the **Schedule Now** button against each Resource Scheduler recommendation, or you can use the Scheduler dashboard. To learn about how to schedule and using the Scheduler dashboard see the next section.

Scheduler Dashboard
===================

The nOps nSwitch resource scheduler is driven by the EventBridge, when you create a schedule it is the EventBridge that makes it possible to turn resources and databases off when they are not being used.

To create a schedule go to **nOps > nSwitch** dashboard and click **\+ Create New nSwitch**:

![](/tmpimg/sol-new-sched.png)

When creating a schedule you can define a group of resources and set an EventBridge as a target for this schedule:

![](/tmpimg/sol-create-sched.png)

Let’s say resources are only being used Monday to Friday 8am to 8 pm and not being used at other times, you can schedule for them to start and stop at the time when they are being used to save costs.

nOps will continue to update the nSwitch recommendations for the machines that could be shut down. Based on these recommendations you can define a new schedule and add the recommended to an existing schedule group.