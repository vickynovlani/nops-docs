---
title: View and Manage Workloads
parent: Workload
grand_parent: User Guides
nav_order: 3
layout: default
---

# View and Manage Workloads

### View and Manage Workloads using the dashboard ###

Workloads are a collection of resources that include your compute resources and comprise a basic unit. A workload should contain all of the resources (EBS or EC2 volumes, S3 buckets etc.) and specify all of the Regions where these resources live.

This article contains the following information:

Why create a workload?

[Viewing a Workload using the Workload Summary tab](#viewing-a-workload-using-the-workload-summary-tab)

[Compliance Ops](#compliance-ops-tab)

## **Why create a workload?** ##
==========================

Creating a workload lets you define competencies, lenses, and frameworks for a workload environment in order _to get contextual recommendations_, targeted assessments and detailed reports.

If you are new to nOps you may find that a Workload has already been created for you. The workload contains all of the regions where you currently have compute resources for the accounts you have shared with nOps.

**Recommendation:** nOps recommends that you create a Production workload that contains all of the compute and other resources used for your Production environment. This workload should be assessed periodically using the AWS [Well-Architected review](#h_6bfa611d28).

You can group different AWS resources in a workload to assess specific services. Create workloads to monitor and report on different parts of your Cloud Architecture. For example, a Production Workload that is comprised of all Production computing resources and regions, or a Dev-ops workload that contains only dev-ops computing resources and regions.

Click the link for information about [How to Create a Workload](#h_356d3c2255)

## **Viewing a Workload using the Workload Summary tab** ##
=====================================================

From the **Workloads** tab, click on a workload to view detailed information.

The **Workload Summary** displays the information using charts.

Click the **arrow** on a chart to see details about that Resource type or click **See All** at the bottom of each chart.

[![](https://downloads.intercomcdn.com/i/o/480254286/a5945ffbbc81b2b702cf1d6e/image.png)](https://downloads.intercomcdn.com/i/o/480254286/a5945ffbbc81b2b702cf1d6e/image.png)

Click an item in the key as seen below to remove it from the chart.

[![](https://downloads.intercomcdn.com/i/o/497008742/9aaff79bfa35a500d78bec06/image.png)](https://downloads.intercomcdn.com/i/o/497008742/9aaff79bfa35a500d78bec06/image.png)

**Click any section of a chart** to view the complete list of that item on the **Resources List** page. Click an item in the bar to view information about that specific resource. You can also use the **filters** or **search** options on the top right of the list. These selections and available options will change based on the type of resource you view.

[![](https://downloads.intercomcdn.com/i/o/497012426/2308dc2d78846b9759402340/image.png)](https://downloads.intercomcdn.com/i/o/497012426/2308dc2d78846b9759402340/image.png)

Workloads can be viewed in the following ways:

Resources Summary

Displays data about Total Resources, Violations, Reserved Instances and Autoscaling

[![](https://downloads.intercomcdn.com/i/o/497007805/6ba206ae778db5f1b8c888dd/image.png)](https://downloads.intercomcdn.com/i/o/497007805/6ba206ae778db5f1b8c888dd/image.png)

Resources by Regions

[![](https://downloads.intercomcdn.com/i/o/480252038/31215df64ce103fca52cca3e/image.png)](https://downloads.intercomcdn.com/i/o/480252038/31215df64ce103fca52cca3e/image.png)

Resources by Cloud Services

[![](https://downloads.intercomcdn.com/i/o/497586185/159a6b5ec1cd5b4d20c6e57a/image.png)](https://downloads.intercomcdn.com/i/o/497586185/159a6b5ec1cd5b4d20c6e57a/image.png)

Resources by Service Category

[![](https://downloads.intercomcdn.com/i/o/497585515/40e4b325fca1f1f4e17e6c8e/image.png)](https://downloads.intercomcdn.com/i/o/497585515/40e4b325fca1f1f4e17e6c8e/image.png)

Tagged and Untagged Resources

[![](https://downloads.intercomcdn.com/i/o/497588385/70301bee88aa8a0bb61515f1/image.png)](https://downloads.intercomcdn.com/i/o/497588385/70301bee88aa8a0bb61515f1/image.png)

Click the **Compliance Ops** tab to change an AWS Lens or Compliance Framework associated with the Workload.

## **Compliance Ops tab** ##
======================

The Compliance Ops tab allows you to change your workload to select or remove additional Lenses and Compliance Frameworks. It contains the following sections:

### Lenses Summary ###
--------------

Contains **Assessment** links and downloadable **Reports** associated with Lenses and Compliance Frameworks.

Integrated reports contain insights and assessments about the selected workload. It walks you through the process of creating and evaluating improvement plans and budgets to plan and track your monthly or yearly spend.

**nOps WAFR (AWS Well-Architected) Report**

Is created based on your answers to questions about the 6 AWS Well-Architected Framework, 'pillars'. For more information about the pillars see: [The Six Pillars of the Framework.](https://wa.aws.amazon.com/wat.pillars.wa-pillars.en.html)

The report lets you review the state of your workloads and compares them to the latest AWS architectural best practices. The information is based on the AWS tools developed to help cloud architects build secure, high-performing, resilient, and efficient application infrastructure. To ensure compliance, Well Architected Reviews must be conducted on your production workload on a periodic basis. After the review, prioritize the remediation of any issues identified for you.

**Foundational Technical Review Report**

This report is based on the lens types selected by you and ensures that your cloud deployment meets the requirements of the lens/es.

### Top Recommendations ###
-------------------

When you create a workload nOps makes recommendations based on the workload priority, and provides details about what to **Fix** based on your answers. Click **See Details** for more information. Click **Fix** to upload the policy document (or enter a link) for remediation. Then click **Upload & Fix** to upload the document to the **Compliance Documents** data repository.

[![](https://downloads.intercomcdn.com/i/o/497021789/f799b9f62ee6e3e1b977993a/image.png)](https://downloads.intercomcdn.com/i/o/497021789/f799b9f62ee6e3e1b977993a/image.png)

For example if you selected a **WAFR** (Well-architected framework) lens, nOps may recommend that you upload a reliability incident playbook. Note that creating a workload on an _existing_ AWS account automatically selects the WAFR Review for you.

All AWS accounts should periodically undergo a WAFR review.

### Compliance Documents ###
--------------------

You can upload documents related to a Workload (or use drag and drop). nOps organizes these documents as you upload them. You can find them easily and in one place. The Compliance Documents repository allows you to track and maintain governance for your cloud environment.

See Also Links:

[How to Create a Workload](./create-workloads)  
[How to add or change Resources in Workloads](./add-new-resources-to-workloads)