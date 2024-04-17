---
title: EC2 and ASG Rightsizing with nOps with DataDog integration
keywords: savings, recommendations, datadog, essentials, rightsizing
tags: [essentials, rightsizing]
sidebar: mydoc_sidebar
permalink: ec2-asg-rightsizing-with-nops-using-datadog.html
folder: Essentials
series: [Essentials, Rightsizing]
weight: 2.0
---

# Overview

The nOps Essentials Rightsizing feature is designed to help organizations optimize their AWS EC2 and AWS ASG resources for cost efficiency without sacrificing performance. By analyzing detailed utilization metrics from the Datadog Agent, such as CPU, memory, and network usage over a specific timeframe, nOps generates customized recommendations to downsize EC2 instances and ASG where possible.

To ensure accuracy and relevance, only resources with at least 15 days of data within a 30-day slot are considered for rightsizing recommendations.


### Getting Started

#### Prerequisites

- A functioning Datadog integration with metrics collection enabled for your EC2 and ASG resources.

- EventBridge for Essentials Rightsizing configured across all your AWS accounts.


#### Instructions

Step 1: Datadog Integration

To begin generating rightsizing recommendations, ensure that your environment is integrated with Datadog. Follow the [Datadog integration guide](https://help.nops.io/integrate-datadog-with-nops-platform.html) closely to set up and start metrics collection from your resources.

Step 2: Configure EventBridge for Essentials Rightsizing

Configure EventBridge for Essentials Rightsizing for all your accounts by following the provided [guide](https://help.nops.io/essentials-storage-rightsizing-eventbridge-setup.html). This step is crucial for enabling the rightsizing feature to communicate and implement changes within your AWS environment.

Step 3: Viewing Recommendations

After setting up Datadog and EventBridge as instructed, rightsizing recommendations should appear on the Rightsizing page within 24 hours of completing the Datadog integration. Navigate to this page by selecting the **Essentials** tab from the main menu, then choosing **Rightsizing**.

The Rightsizing Recommendations page contains two separated tabs called **EC2 Rightsizing Recommendations** and **ASG Rightsizing Recommendations**.

These pages display:

- Recommendations Summary

- AWS Account Name

- Resource ID and Name

- Environment (Env)

- Current and Recommended Instance Type

- Region

- Estimated Annual and Monthly Savings

![](https://photos.app.goo.gl/hGMSHBVbS4kaKXWd7)
![](https://photos.app.goo.gl/FayMsJRLVcsuvYW4A)

Each EC2 listing includes an **Action** button for further steps.

Step 5: Rightsizing Your EC2 Instances

To rightsize an instance or group of instances, click the **Action** button associated with your chosen recommendation group. This will take you to a detailed page where, assuming EventBridge is properly configured, your account and target event bridge are pre-selected. Verify the resource details and schedule the trigger time if needed. Otherwise, “Now” is selected by default (this will automatically schedule rightsizing to take place in 10 minutes from now). Click the Rightsize button to proceed.

![](https://photos.app.goo.gl/rV6RKaaU85Ydbnc97)

Step 6: Scheduling with Summary

You will be redirected to the Summary page, where a rightsizing operation is scheduled. Here, you can monitor or cancel the scheduled rightsizing operation within 10 minutes before it triggers.

![](https://photos.app.goo.gl/ZzbzDh7iqSv3ExhB8)

Step 7: Finalizing and Verification

Once the rightsizing operation is triggered, it cannot be canceled. To verify the changes, log into your AWS account and check the instance sizes against the recommendations provided. This ensures that the rightsizing has been completed as expected.



## Notes & FAQs

- Rightsizing requires a downtime, AWS has no SLA but in our experience it takes 2-3 minutes. It depends on the size of the instance.
- Rightsizing currently has recommendations for only downsizing, however, potentially we can add upsizing recommendations as well in future.
- Rightsizing can fail for instance with Encrypted EBS volumes or instances where hibernation is enabled. Currently we mark those instances on the recommendations page in the UI and disabled them from getting rightsized. We are working on a feature to support those types as well.


<br/><br/>

{% include custom/series_related.html %}