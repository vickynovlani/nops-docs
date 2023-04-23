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

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778727/7ddc63d8fb65fccd38166c38/6QygeL5g7nKjdAUO9vpmFGqvOeqKHgPJv0rwvwkYNu9FmC00Vg0SodmpQ8atXtLulr52WKmjyyJSwMqyLbFDhGpsR3GdMel-PCP15aK4r7QGE6c2gPr0Olqv9CHibvXc6TfGRCLyhxl3Vk10xVaUMs0cA149zTt7U5IXGRfdPXsaff_qe6OqOrbwBw)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778727/7ddc63d8fb65fccd38166c38/6QygeL5g7nKjdAUO9vpmFGqvOeqKHgPJv0rwvwkYNu9FmC00Vg0SodmpQ8atXtLulr52WKmjyyJSwMqyLbFDhGpsR3GdMel-PCP15aK4r7QGE6c2gPr0Olqv9CHibvXc6TfGRCLyhxl3Vk10xVaUMs0cA149zTt7U5IXGRfdPXsaff_qe6OqOrbwBw)

Once the EventBridge integration is set up, you can create event sources directly from the nOps application and deploy them to any account and region that you’ve connected to nOps.

To integrate your AWS EventBridge with nOps, log in to nOps and click **User Avatar > Organization Settings > Integrations > EventBridge**. In the _Event Bridge_ tab click **\+ Create EventBridge**:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778736/a6b6a4b765408d2db819b009/YhCkG7AgPCTHu4a5rlVp1Bk7-xDSN6-JBgkJdmR5izqqtKEXIAuXLiUHBtLiH63gVl1fiypzDbjUrK9xv6JuQ2XZEuCss3iryDqBKg5zsU7UbjiTXbBY0sAu9J6F-26HkDysJIqUADmi8wd8N9hxePpp4P-po1jqQ7eT5qfl9_509OLHhpML9ur2EA)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778736/a6b6a4b765408d2db819b009/YhCkG7AgPCTHu4a5rlVp1Bk7-xDSN6-JBgkJdmR5izqqtKEXIAuXLiUHBtLiH63gVl1fiypzDbjUrK9xv6JuQ2XZEuCss3iryDqBKg5zsU7UbjiTXbBY0sAu9J6F-26HkDysJIqUADmi8wd8N9hxePpp4P-po1jqQ7eT5qfl9_509OLHhpML9ur2EA)

In the **Create New Event Bridge** page:

1.  Create a name for this EventBridge.
    
2.  Select the AWS account you want to deploy the EventBridge into. In the AWS accounts list, you will only see the accounts that you onboard into nOps.
    
3.  Select the region you want to deploy the EventBridge into.
    
4.  Click **Create**.
    

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778738/7f7b800874a48065a22771cd/Yfdoy5Ct_uH5Lq1507gwuz3ce75Llq9WOTzWBye8BXXrw1zl2Ak-2eSKYNoLOAdqfXFQ9J5W89gWol6Nq1BncEqCVBqgbCPS9vr6kT2vTAvM2CYxf-2sRCYynswEndZhMotVYktz3W3Bbq0iWZiGnMOGFaPUtnxReBXDZvJQ93S7BFTpDxn9ZSRTwA)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778738/7f7b800874a48065a22771cd/Yfdoy5Ct_uH5Lq1507gwuz3ce75Llq9WOTzWBye8BXXrw1zl2Ak-2eSKYNoLOAdqfXFQ9J5W89gWol6Nq1BncEqCVBqgbCPS9vr6kT2vTAvM2CYxf-2sRCYynswEndZhMotVYktz3W3Bbq0iWZiGnMOGFaPUtnxReBXDZvJQ93S7BFTpDxn9ZSRTwA)

When you click **Create**, nOps will deploy the EventBridge into your selected AWS account and region by creating an event bus in the selected AWS account.

To see the event bus that nOps just created, go to **AWS > Amazon EventBridge > Event buses > Custom event bus**.

The next step is to add an EventBridge target into Webhooks.

Adding EventBridge Target into nOps Webhooks
============================================

nOps has a Webhook for almost every cost optimization rule in the nOps environment.

When you create a Webhook, anytime an associated event is fired a message will be sent to either the endpoint you define or the EventBridge that you create.

To add an EventBridge target into nOps Webhooks, go to **User Avatar > Organization Settings > Integrations > Outgoing Webhooks**. In the _Outgoing Webhooks_ tab, click **\+ Create New Webhook**:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778740/54e0d66bebf9e1b88c2c886b/GRtLCuY1uavGyOtEGldQv0816ej9xV6NpZRAZour-hAAjkEiCFMAUVP7d3S5QvNZ8Jrcc1qhKuwpr69I35-DA8uzGv0mYEZwCtZDqyy5KwM9BplK4g-0EvDrE29Gf0yCL0_AhEgS2kSA49PP4i1Fpl141f0l6YGsuMUboQ_-kUG4Mw4ihdtsnJ2MoA)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778740/54e0d66bebf9e1b88c2c886b/GRtLCuY1uavGyOtEGldQv0816ej9xV6NpZRAZour-hAAjkEiCFMAUVP7d3S5QvNZ8Jrcc1qhKuwpr69I35-DA8uzGv0mYEZwCtZDqyy5KwM9BplK4g-0EvDrE29Gf0yCL0_AhEgS2kSA49PP4i1Fpl141f0l6YGsuMUboQ_-kUG4Mw4ihdtsnJ2MoA)

In the **Create New Webhook** page:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778744/9ff6e8349d3fc388ca0359a4/cO4dlXgZM3XKLKN0IjBu8KU-FgcVFaQrI9CGgML9F_Nh3j6NP9BY3Ot4B_JIdl6x12zcl8QXV3vOrpfxwuLMe0Lmw9_8pfjVBB5MCLkwCo6CuRNtWvc_fxXOo1Z_2eeOACvXYLfwT-eIb9H2FcAZEjmiFG5dcY4uCeQ6rFMumQOK1liR9tAsBXRCkg)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778744/9ff6e8349d3fc388ca0359a4/cO4dlXgZM3XKLKN0IjBu8KU-FgcVFaQrI9CGgML9F_Nh3j6NP9BY3Ot4B_JIdl6x12zcl8QXV3vOrpfxwuLMe0Lmw9_8pfjVBB5MCLkwCo6CuRNtWvc_fxXOo1Z_2eeOACvXYLfwT-eIb9H2FcAZEjmiFG5dcY4uCeQ6rFMumQOK1liR9tAsBXRCkg)

1.  Create a **name** for the Webhook.
    
2.  Select an **Event**. Notice that the Event option has two fields, in the first field you need to select the event category, and in the second you need to select the actual event.
    
3.  Select an **Endpoint**, it can be either a simple Endpoint (Target URL) or an **EventBridge**. In the scope of this documentation we are only going to select the EventBridge option. Selecting this option will send the Webhook to your EventBridge.
    
4.  Select an EventBridge from the list. The list consists of all EventBridges that you create in **nOps > Organization Settings > Integrations > EventBridge** tab.
    
5.  Click **Save**.
    

EventBridge Automatic Configuration Walkthough
==============================================

When you create an EventBridge in nOps, nOps will automatically create an event bus in your selected AWS account. To see the event bus that nOps automatically created, go to **AWS > Amazon EventBridge > Event buses > Custom event bus**.

Once, you have configured the webhook, come back to the **nOps > Organization Settings > Integrations > EventBridge** tab and click **Launch Stack** against the EventBridge that you created:

[![](https://downloads.intercomcdn.com/i/o/616502861/841e31a6ccc7a4924796734a/2022-11-14_21-24-44.png)](https://downloads.intercomcdn.com/i/o/616502861/841e31a6ccc7a4924796734a/2022-11-14_21-24-44.png)

* * *

**Note:** Before you click **Launch Stack**, make sure that you are logged into the AWS account that you used for the EventBridge. You also need to make sure that the account region is the same as the one you specified while creating the EventBridge.

* * *

When you click Launch Stack, you will be redirect to **AWS > CloudFormation > Stacks > Create stack:**

[![](https://downloads.intercomcdn.com/i/o/616522470/9ade4c6c957036f6944c8d70/2022-11-14_22-36-31.png)](https://downloads.intercomcdn.com/i/o/616522470/9ade4c6c957036f6944c8d70/2022-11-14_22-36-31.png)

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

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778745/878e182b92569aded9324962/1jvSLtBjX2OwVrC7Nyp3XJfAt72pDAxo7XmH65E1MPWHR-w3Jy0yi7_RNkg0IWH-aHLStEowgNStuK7Bq5av_s7NyvdMeaf3qjhC9SBoLIyJYbyi6woLyvnUNX4mSkiXLoDjg6vmE-dwTNYy-_Rs86DZZ0Si_Qk1RODhisqpKewo-hutlEmWdW-gEQ)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778745/878e182b92569aded9324962/1jvSLtBjX2OwVrC7Nyp3XJfAt72pDAxo7XmH65E1MPWHR-w3Jy0yi7_RNkg0IWH-aHLStEowgNStuK7Bq5av_s7NyvdMeaf3qjhC9SBoLIyJYbyi6woLyvnUNX4mSkiXLoDjg6vmE-dwTNYy-_Rs86DZZ0Si_Qk1RODhisqpKewo-hutlEmWdW-gEQ)

When you click next, the next step is **Build Event Pattern**. In the **Build** **Event pattern** section, select the **Custom patterns (JSON editor).** In this example we will use the following patterns:

{

"detail-type": \[ {

"anything-but": "initializing"

} \]

}

For the full list of nOps Event Patterns, see **nOps EventBridge Event Patterns**.

Enter the **Event pattern** and click **Next**:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778747/4d1503304871a03f5de9592a/KIkIUjagpA8TVllO5cSVjbcR-FvuQbTGI_Y1IDp4j2Sw-uQGzTylZOoaeHTIkC-bixFpSZzuYzBxf7e6fJsXGQ8B1rLy1yTANtpvuZt0fyB_cvdFDJnebDIJ3TOZ_LZnmcBJ27sAOLtTg6qA0TPRQcVVObhLV54EuloQ5uimL1Q8cG9gslxTrDShTA)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778747/4d1503304871a03f5de9592a/KIkIUjagpA8TVllO5cSVjbcR-FvuQbTGI_Y1IDp4j2Sw-uQGzTylZOoaeHTIkC-bixFpSZzuYzBxf7e6fJsXGQ8B1rLy1yTANtpvuZt0fyB_cvdFDJnebDIJ3TOZ_LZnmcBJ27sAOLtTg6qA0TPRQcVVObhLV54EuloQ5uimL1Q8cG9gslxTrDShTA)

The next step is **Select target(s).**

In the target list, there are a lot of targets that you can select. In the future we will also provide numerous Lambda functions. In the scope of this example, we will select the SQS queue and select the queue you created in the beginning of the walkthrough, and then click **Next**:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778753/b56da382ac86ec1412796b1b/v59B6EgXq6f8ZhV06-wFBUqz3aeoYkPyXDFTNNTLtw_yczmSe-tgOkIswT4fBhXdgWouGNOmwL_M2Rt2Gcd2BM6uWaKCXdVIPyTeh9C4SZc160n-swS50gpIhffHSI8aM9FzXu8A5us4YEjZB6jqWvEQIlYR5LHN96wNG9kwV_5PAg7PzCHWmIS9dQ)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778753/b56da382ac86ec1412796b1b/v59B6EgXq6f8ZhV06-wFBUqz3aeoYkPyXDFTNNTLtw_yczmSe-tgOkIswT4fBhXdgWouGNOmwL_M2Rt2Gcd2BM6uWaKCXdVIPyTeh9C4SZc160n-swS50gpIhffHSI8aM9FzXu8A5us4YEjZB6jqWvEQIlYR5LHN96wNG9kwV_5PAg7PzCHWmIS9dQ)

The next section is the **Configure tags** section, which is optional. In the scope of this example, you don’t need to add any tags, simply click **Next**:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778756/403a07e5271192189070389f/AIDRND2CiVTD7o2shZ5-c8CTVDh7hF2jGPWlJ0UVmV38kocfUQBK2XiHGseCGYD_fR9CyWvFqRDxTN8pbnBmZsWSNrkQlwXGLa4voF5BM6zkBdXPaOTJYF0hDxBO1h1jTwpcIbkum_yWYkDuZJ5PBuiqOU0MpowbdMWPP0zieroMc4sowJ4Z4CQ5wA)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778756/403a07e5271192189070389f/AIDRND2CiVTD7o2shZ5-c8CTVDh7hF2jGPWlJ0UVmV38kocfUQBK2XiHGseCGYD_fR9CyWvFqRDxTN8pbnBmZsWSNrkQlwXGLa4voF5BM6zkBdXPaOTJYF0hDxBO1h1jTwpcIbkum_yWYkDuZJ5PBuiqOU0MpowbdMWPP0zieroMc4sowJ4Z4CQ5wA)

The next section is the final section, **Review and create**. In this section review the rule and click **Create Rule**.

Send Demo Message
-----------------

In order to check if the EventBrdige was configured correctly, we will send a test message to Amazon SQS via the Webhook that we created. To send the test message , go to **nOps > Organization Settings > Integrations > Outgoing Webhooks** and click the icon highlighted below against the Webhook:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778759/f8ccdb76a85c70ccfef060a7/a4pw5rRFLiiRRANDnfslkA7oXoi8pxnRynTmLe2xsbHioKYaDxek5SrUIgnsUzBFv9Hi-hTNsSQc4YNB44UNjROoa8c3XfcfGkCv1vDKzKxFZTDPE6W19FkSDru7Vz29RowoMcO_eGfyp-V_zceNbCk4f7seswyEm1lX8NMbUPdPn7m6UhUqW2c3kQ)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778759/f8ccdb76a85c70ccfef060a7/a4pw5rRFLiiRRANDnfslkA7oXoi8pxnRynTmLe2xsbHioKYaDxek5SrUIgnsUzBFv9Hi-hTNsSQc4YNB44UNjROoa8c3XfcfGkCv1vDKzKxFZTDPE6W19FkSDru7Vz29RowoMcO_eGfyp-V_zceNbCk4f7seswyEm1lX8NMbUPdPn7m6UhUqW2c3kQ)

Now, to check if the message is received, go to your **AWS > Amazon SQS > Queues > \[The queue you created\]**. In the queue, click the **Send and receive messages** button:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778760/b6b1358929dc332d0920275c/S24fUxq2N3oJ4ZJoy0EN-appJHG0zZkO6KuCYJjYghF-7DKE5XCKdnXW5gOdjWr0gQKj1XTQlrGN-1gTZprM0M2Vf2z_WfNeWHEdFDEJIOW7QNY3zwxX3_D-wzuJ_SFjrpHwQ6s74xJmnZykNE88RPRAZJXFFqEQjhDccXk_eiWTONAhiiVA4kkaRA)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778760/b6b1358929dc332d0920275c/S24fUxq2N3oJ4ZJoy0EN-appJHG0zZkO6KuCYJjYghF-7DKE5XCKdnXW5gOdjWr0gQKj1XTQlrGN-1gTZprM0M2Vf2z_WfNeWHEdFDEJIOW7QNY3zwxX3_D-wzuJ_SFjrpHwQ6s74xJmnZykNE88RPRAZJXFFqEQjhDccXk_eiWTONAhiiVA4kkaRA)

On the **Send and receive messages** page, click the **Poll for messages** button:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778765/0a3d9d565732c053bd9069a6/d8zC86_zcpB1s_E312lDDdk5eAAYqiQpLBWW0zyBU4jC6QedgwiC4f5XLqJP-XCjP-LpX-V_x8jjmCnk0BzpgioBzrkSeXWs2o7RoQn9ogzXawK4CLTjymMLxVbULQHwUvsPymmF4_PkOlzI5GqUSHUcb7XBUgtSwjAg1bD6cgIYAX40z1VQxSJyWQ)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778765/0a3d9d565732c053bd9069a6/d8zC86_zcpB1s_E312lDDdk5eAAYqiQpLBWW0zyBU4jC6QedgwiC4f5XLqJP-XCjP-LpX-V_x8jjmCnk0BzpgioBzrkSeXWs2o7RoQn9ogzXawK4CLTjymMLxVbULQHwUvsPymmF4_PkOlzI5GqUSHUcb7XBUgtSwjAg1bD6cgIYAX40z1VQxSJyWQ)

If the configuration was successful, you will receive the test message in the **Messages** section.

nSwitch Recommendations
==================================

nOps identifies opportunities to turn computers, resources, instances, and databases off at certain hours. Expensive environment when not being used still costs if they are not turned off.

nOps looks at your usage statistics and makes recommendations to schedule resources for availability during a specific time frame when they are expected to be used. You can then schedule these resources to start and stop using nSwitch.

To see the nSwitch Recommendations and the potential savings that scheduling resources can provide, go to **nOps > ShareSave Dashboard > nSwitch**:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778773/54586e598089e4b20ebf924e/ABakHRCKrpesgRlEdouZ633KOq14dO8OcQGcuTKj8ZlQSsBAjy_lk-4uv3OWmBjTLhpEE-EQkjdLPHHxJ8QpuEtLoBeUb8cjYJAi65PKumonOzfVlgSXwBlxZHmgTMicTXMXLrflJG8uPGseQp63FH-2HNjsBbfaDHeciMULIc3TJrqo1C3KRtHQDQ)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778773/54586e598089e4b20ebf924e/ABakHRCKrpesgRlEdouZ633KOq14dO8OcQGcuTKj8ZlQSsBAjy_lk-4uv3OWmBjTLhpEE-EQkjdLPHHxJ8QpuEtLoBeUb8cjYJAi65PKumonOzfVlgSXwBlxZHmgTMicTXMXLrflJG8uPGseQp63FH-2HNjsBbfaDHeciMULIc3TJrqo1C3KRtHQDQ)

Click on an opportunity to expand it. nOps will provide you with a recommendation of schedule against each instance type and an estimate of the potential savings:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778778/b5a01b09790b1f8238af06c4/ZUiFD8x0seAeDFmYNy4x-wRox9NJ8tcSBXb7wq5C7qrPsXdtqcmODuAysaW0aTZEGe9xsLG9vE4UXX0A_eg62SKJ83YbfoJPDMVwklcBbru4gQLGT26qQFsGSaoRQnpAb2KM4kQRBiNkzDH7Fp6HDSknvd5fM2VRdMLys3WNm5T4SsrqNo3el7GhKA)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778778/b5a01b09790b1f8238af06c4/ZUiFD8x0seAeDFmYNy4x-wRox9NJ8tcSBXb7wq5C7qrPsXdtqcmODuAysaW0aTZEGe9xsLG9vE4UXX0A_eg62SKJ83YbfoJPDMVwklcBbru4gQLGT26qQFsGSaoRQnpAb2KM4kQRBiNkzDH7Fp6HDSknvd5fM2VRdMLys3WNm5T4SsrqNo3el7GhKA)

You can either create a schedule directly from the Resource Scheduler section by clicking the **Schedule Now** button against each Resource Scheduler recommendation, or you can use the Scheduler dashboard. To learn about how to schedule and using the Scheduler dashboard see the next section.

Scheduler Dashboard
===================

The nOps nSwitch resource scheduler is driven by the EventBridge, when you create a schedule it is the EventBridge that makes it possible to turn resources and databases off when they are not being used.

To create a schedule go to **nOps > nSwitch** dashboard and click **\+ Create New nSwitch**:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778781/cd296ad2f3a7a6988d76467c/V_xNdWpnr-mkjoz42xjclKqsBwINbyOchGWe_1o5kFzQjVC2-jmFHd2rqYHYJUAsj_xGc9iK5rkvRC0p57z7JvikS5_EgXGVGo_MNN3fk-qrXhrO0c6_hz7oWG5hOGcMOfiDRau2x_ug-bQm1R91wP0AyhxBBQaaPTC1iL1300G0LiU7cTMzPU5T_g)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778781/cd296ad2f3a7a6988d76467c/V_xNdWpnr-mkjoz42xjclKqsBwINbyOchGWe_1o5kFzQjVC2-jmFHd2rqYHYJUAsj_xGc9iK5rkvRC0p57z7JvikS5_EgXGVGo_MNN3fk-qrXhrO0c6_hz7oWG5hOGcMOfiDRau2x_ug-bQm1R91wP0AyhxBBQaaPTC1iL1300G0LiU7cTMzPU5T_g)

When creating a schedule you can define a group of resources and set an EventBridge as a target for this schedule:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778784/2d4e26d37f75b0c477cfe568/Ob54VZzYPc4nA1WhFsANwpti4NzRDwuCkMr4Dq_o3f02s_0_mi8Ght6ebroXN0knidWxBFTvtG96odG4cx9U4O1sdzdhggxvaRWpTgc98tAXaCFnkWZEI4lSCCbMihIOyIbO71jLgHNnnz6feDYHe73f1Qbct7zcT0bZhhnrKs0Ids9linjXNMuJfQ)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/594778784/2d4e26d37f75b0c477cfe568/Ob54VZzYPc4nA1WhFsANwpti4NzRDwuCkMr4Dq_o3f02s_0_mi8Ght6ebroXN0knidWxBFTvtG96odG4cx9U4O1sdzdhggxvaRWpTgc98tAXaCFnkWZEI4lSCCbMihIOyIbO71jLgHNnnz6feDYHe73f1Qbct7zcT0bZhhnrKs0Ids9linjXNMuJfQ)

Let’s say resources are only being used Monday to Friday 8am to 8 pm and not being used at other times, you can schedule for them to start and stop at the time when they are being used to save costs.

nOps will continue to update the nSwitch recommendations for the machines that could be shut down. Based on these recommendations you can define a new schedule and add the recommended to an existing schedule group.