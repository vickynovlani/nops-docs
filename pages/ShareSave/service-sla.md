---
title: SLAs for Spot Cost Consideration Engine
keywords: savings, recommendations, sharesave, spot
tags: [savings, recommendations, sharesave]
sidebar: mydoc_sidebar
permalink: service-sla.html
folder: ShareSave
---

**Effective Date:** September 7th, 2023

**1. Introduction**

This Service Level Agreement (SLA) outlines the commitment of nOps to ensure the reliability and availability of Spot Instances within our Cost Consideration product for our valued customers. We understand the importance of your workloads running on Spot Instances and are dedicated to delivering a superior service experience.

**2. Scope**

This SLA applies to customers who have connected their Amazon Elastic Kubernetes Service (EKS), AutoScaling Group, or Databricks job to our Cost Consideration product ("Customers").

**3. Reliability Guarantee**

Service Provider guarantees the following:

- **Termination Event Responsiveness:** If a Customer's workload is placed on a Spot Instance that receives a termination event, and the Service Provider fails to react to the event at least one hour in advance, Service Provider will compensate the Customer.

**4. Compensation**

In the event of a failure to meet the Termination Event Responsiveness guarantee, Service Provider will provide compensation as follows:

- Service Provider will pay for the terminated AWS Spot Instance's hourly usage fee for up to the entire month of the termination.

**5. Terms and Conditions**

To qualify for compensation under this SLA, the following conditions must be met:

- The Customer's workload must be connected to the Cost Consideration product and meet the eligibility criteria.
- The customer’s workload must select a minimum of four unique AWS instance families to allow for workload diversification.
- The termination event must occur due to reasons beyond the Customer's control.
- The Customer will not be required to report the SLA event, it will be automatically calculated in the event of termination.
- Compensation will be provided as a credit to the Customer's account.

**6. Exclusions**

This SLA does not cover:

- Termination events resulting from Customer actions or misconfigurations.
- Downtime or termination events related to any third-party services or components.
- Termination events resulting from AWS outages or interruptions.

**7. Reporting an Incident**

To report an incident and request compensation under this SLA, the Customer must contact our support team through the designated support channel, providing all necessary details of the incident, including timestamps, instance IDs, and other relevant information.

**8. Review and Amendment**

Service Provider may review and amend this SLA from time to time. Any changes will be communicated to the Customer in advance.

**9. Conclusion**

Service Provider is committed to providing reliable Spot Instances within our nKS product. We understand the importance of your workloads and strive to deliver the best service possible. If you have any questions or concerns about this SLA, please contact our support team for clarification.

Docs site

**Introducing the Cost Consideration Spot Instance Reliability SLA**

We are excited to announce a new and unique Service Level Agreement (SLA) that sets us apart in the market and underscores our commitment to your success with our Cost Consideration  engine.

**What is it?**

Our new SLA focuses on ensuring the reliability of Spot Instances within our Cost Considration product for customers who have connected their Amazon Elastic Kubernetes Service (EKS), AutoScaling Group, or Databricks job to our service. ***You can run your workload on spot with the same confidence as AWS on-demand.*** 

**What does it guarantee?**

In simple terms, if we place your workload on an instance that receives a termination event, and we fail to replace that instance before termination, we will cover the terminated AWS instance's hourly usage fee for up to the entire month of the termination. Yes, you read that right – we've got you covered!

**Why is this different?**

This SLA goes beyond the ordinary and demonstrates our unwavering commitment to your success and satisfaction. We understand how critical Spot Instances are for your workloads, and we want to ensure you have peace of mind.

**Do I need to report an incident?**

Never. Any credit will be automatically applied as part of our monthly billing cycle. If, by any chance, you think we missed a credit, simply report the incident to our support team within 72 hours of final monthly billing, and we'll take care of the rest.

**When does it take effect?**
The nKS Spot Instance Reliability SLA is effective from September 6th, and we can't wait to show you the difference it makes in your experience with our service.


**Are there any other considerations?**

- Does not apply in the event of an Amazon service outage impacting the region in the termination.
- You must diversify by selecting at least five instance families as part of your node template configuration.

At nOps, we are always striving for excellence, and this SLA is another step in that direction. If you have any questions or need further clarification, please don't hesitate to reach out to our support team.