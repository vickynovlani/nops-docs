---
title: EC2 Rightsizing with nOps with DataDog integration
keywords: savings, recommendations, datadog, essentials, rightsizing
tags: [essentials]
sidebar: mydoc_sidebar
permalink: ec2-rightsizing-with-nops-using-datadog.html
folder: Essentials
series: [Essentials, Rightsizing]
weight: 2.0
---

# Overview

The nOps EC2 Rightsizing feature is designed to help organizations optimize their AWS EC2 instances for cost efficiency without sacrificing performance. By analyzing detailed utilization metrics from the Datadog Agent, such as CPU, memory, and network usage over a specific timeframe, nOps generates customized recommendations to downsize EC2 instances where possible.

To ensure accuracy and relevance, only resources with at least 15 days of data within a 30-day slot are considered for rightsizing recommendations.


### Getting Started

#### Prerequisites

- A functioning Datadog integration with metrics collection enabled for your EC2 instances.

- EventBridge for Essentials configured across all your AWS accounts.


#### Instructions

Step 1: Datadog Integration

To begin generating rightsizing recommendations, ensure that your environment is integrated with Datadog. Follow the [Datadog integration guide](https://help.nops.io/integrate-datadog-with-nops-platform.html) closely to set up and start metrics collection from your EC2 instances.

Step 2: Configure EventBridge for Essentials

Configure EventBridge for Essentials for all your accounts by following the provided [guide](https://help.nops.io/scheduler-eventbridge-setup.html). This step is crucial for enabling the rightsizing feature to communicate and implement changes within your AWS environment.

Step 3: Viewing Recommendations

After setting up Datadog and EventBridge as instructed, rightsizing recommendations should appear on the Rightsizing page within 24 hours of completing the Datadog integration. Navigate to this page by selecting the **Essentials tab** from the main menu, then choosing **Rightsizing**.

The Rightsizing Recommendations page currently supports EC2 instances Only.

This page displays:

- AWS Account Name

- Instance ID and Name

- Environment (Env)

- Current and Recommended Size

- Region

- Estimated Annual and Monthly Savings

Each listing includes an **Action** button for further steps.

![](https://lh7-us.googleusercontent.com/5Vacknqkj5FJ_1VIrPfFdjnKty7rhnOknHqhqNLBwT1TK2PTLeeJp2e71NkQr_aFZf6sJm51yV11DLHMmsiqnrhUZchr-Gjtz2CvXsPyA0vRvbJ2d1A69_Vp5DjC_UkGmNCHq5MK8GJHr-Z_1JLIsNU)

Step 5: Rightsizing Your Instances

To rightsize an instance or group of instances, click the **Action** button associated with your chosen resource. This will take you to a detailed page where, assuming EventBridge is properly configured, your account and target event bridge are pre-selected. Verify the resource details and schedule the trigger time if needed. Otherwise, “Now” is selected by default (this will automatically schedule rightsizing to take place in 10 minutes from now). Click the Rightsize button to proceed.

![](https://lh7-us.googleusercontent.com/r_rbTw7srrt3HH0kLoMLoOmhs1gXtStNw4tbDWt1Azdaup1vBbgDtRcDpWkAghTOvSHJqdfrM3ML4MEA7pusFWvEep0XIluVhLP8SYBw3644VdPUXHUoZQVopuQVNTdAagczspX87l9JRJ3diKETuDE)

Step 6: Scheduling with Summary

You will be redirected to the Summary page, where a rightsizing operation is scheduled. Here, you can monitor or cancel the scheduled rightsizing operation within 10 minutes before it triggers.

![](https://lh7-us.googleusercontent.com/MpIowNiOZyK14N0yq0uRnv6MHdQ_297CdKm7UfKF-ZqBlJJ5-fvEzN7Ohr4wO_fCV33mRvBrD9_UAJauJzstg7aJxLiCIjk70bDl4wBXDhBY6E0XciKNZk4dhidOHuHyvYGWz7__Dj5QZDdFjFrzrlc)

Step 7: Finalizing and Verification

Once the rightsizing operation is triggered, it cannot be canceled. To verify the changes, log into your AWS account and check the instance sizes against the recommendations provided. This ensures that the rightsizing has been completed as expected.



## Notes & FAQs

- EC2 rightsizing requires a downtime, AWS has no SLA but in our experience it takes 2-3 minutes. It depends on the size of the instance.
- EC2 rightsizing currently has recommendations for only downsizing, however, potentially we can add upsizing recommendations as well in future.
- EC2 rightsizing can fail for instance with Encrypted EBS volumes or instances where hibernation is enabled. Currently we mark those instances on the recommendations page in the UI and disabled them from getting rightsized. We are working on a feature to support those types as well.


<br/><br/>

{% include custom/series_related.html %}