---
title: Well-Architected Framework Review
keywords: reporting, assessment, compliance
tags: [compliance, reporting]
sidebar: mydoc_sidebar
permalink: wafr-review.html
folder: UserGuides
---

Well-Architected Framework Review

In this article you will learn how to perform a Well-Architected Framework Review (WAFR) with nOps. This article contains the following information:

- TOC
{:toc}
    

## Getting Started ##
===============

AWS Well-Architected helps cloud architects build secure, high-performing, resilient, and efficient infrastructure for their applications and workloads. Based on five pillars — operational excellence, security, reliability, performance efficiency, and cost optimization — AWS Well-Architected provides a consistent approach for customers and partners to evaluate architectures and implement designs that can scale over time.

To get started, log in to your nOps account and switch to the **Workloads > WAFR** section. In the Workloads section, you can:

1.  [Create a new Workload](#creating-your-first-workload).
    
2.  Filter Workload based on the compliance framework.
    
3.  Search Workloads based on the Workload name.
    
4.  Edit or Delete a Workload.
    
5.  Click on a Workload to go to its [summary page](#workload-summary-view).
    

![](/tmpimg/2022-08-26_23-32-00.png)

## Creating Your First Workload ##
============================

To create a Workload, click the + Create New Workload button at the top-right corner of the screen:

![](/tmpimg/2022-08-17_04-07-19.png)

When you click **“ \+ Create New Workload”** the workload creation panel will appear. Remember that the Workload name cannot be changed once it's created:

![](/tmpimg/2022-08-17_04-11-35.png)

In the Workload creation panel:

* **Workload name** **—** Create a unique identifier/name for your workload. A Workload name cannot be changed once it's created.
    
* **Review types —** Select  the type(s) of review/lens you want to apply on this Workload, for WAFR the review type must always be "_Well-Architected Framework Review (WAFR)_".
    
* **Compliance frameworks —** Select the desired compliance framework — HIPAA, SOC2, or CIS.
    
* **Create workload on your AWS account —** Toggle this button to allows create and sync this workload in your AWS Well-Architected Tool. If you toggle this button:
    
    ![](/tmpimg/2022-08-18_01-01-06.png)
    
    * A new field "**AWS account to save WAFR progress**" is added to the **Create new Workload** panel.
        
    * Well-Architected Framework Review (WAFR) is automatically selected in **Review types** field.
        
    
* **AWS account to save WAFR progress —** Select the AWS account your workload will be written to.
    
* **AWS account to pull resources from —** Select the AWS Account(s) where the resources for your workload live. _All your AWS account associated with nOps will be shown in this list_.
    
* **Select Environment** **—** This defaults to PRODUCTION and defines the environment from an AWS perspective. _Note: Sanctioned Well-Architected Framework Reviews should always be performed on a production workload._ You also have the option to create and select a custom environment.
    
* **Description** **—** A text description of your workload.
    

Once you've filled out the fields, click **Save** to create a Workload with all the resources in the AWS account specified in **AWS account to pull resources from** field**.**

To filter out the resources that are not required for WAFR, use the **Specify Workload Resource** section. To learn more about how to specify workload resources, see the next section.

Defining the Workload Query
---------------------------

After filling out the information, in the **Create new Workload** panel click the gray bar **Specify Workload Resource** to open a query builder:

![](/tmpimg/2022-08-17_04-11-35.png)

The nOps query builder allows you to specify rules that define which resources will be added to the workload. You can change the default settings and specify the filters using the drop-downs:

![](/tmpimg/2022-08-18_00-57-42.png)

In nOps query builder:

* **Regions** **—** Select the region(s) that nOps will pull resources from. _This setting defaults to **All**_.
    
* **AWS Managed Services** **—** Select the AWS service(s) that nOps will include in your workload. _This setting defaults to **All**_.
    
* **Select Tag Name & Select Tag Value** **—** Select the tags that are associate with the resources that you want to include. Only the resources with the selected tags will be included in the workload. When you select a tag in the **Select Tag Name**, the values list in the **Select Tag Value** will update according to the values of the selected tag name.
    
* **\+ Add Another Tag —** Allows you to add multiple tags.
    
* **Note —** Allows you to add a note against this filter.
    

Click **“Save”** to create your workload.

## Workload Summary View ##
=====================

In the **Workloads** section, click on any Workload to go to its summary page. There are 3 tabs in the summary page:

* Diagram
    
* Summary
    
* Compliance Ops
    

When you click on a Workload, you will land on the **Diagram** tab of the summary page.

Diagram Tab
-----------

In the **Diagram** tab of the summary page, you will see the diagrams of your Workload resources segregated at the level of VPCs, regions, and subnets.

You can click on any VPC, region, subnet, or node to see its details. A summary of violations against your selection is shown on the right side of the diagram:

![](/tmpimg/2022-08-18_03-59-24.png)

Summary
-------

In the **Summary** tab, you have an overview of the your Workload:

![](/tmpimg/2022-08-18_04-00-03.png)

In this page you will find:

* **Resource Summary —** In this section you will find the total number of resources, the number of resources with violation, the number of reserved instances, and the number of resources that are a part of _AutoScaling_ in this Workload.
    
* **Resource by Regions —** Shows a donut chart with breakdown of all the regions where your resources belong to. You can hover over the chart to see how many resources you have in each region. You can also click on **See All** to see the full list of resources by region.
    
* **Resource by Cloud Services —** Shows a donut chart with breakdown of the cloud services to which your resource belong to. You can hover over the chart to see how many resources you have in each service. You can also click on **See All** to see the full list of resources by cloud services.
    
* **Resource by Service Category —** Provides a breakdown of resource by service category in the form of a bar chart with services on the Y-axis and the number of resources on the X-axis. You can also click on **See All** to see the full list of resources by service category.
    
* **Tagged and Untagged Resources —** In this section you will find the total number of tags used, tagged resources, and untagged resource in the Workload. This section also shows a bar chart with a breakdown of all the values against each tag. You can hover over the chart to see the values of each tag. You can also click on See All to see the full list of Tags and their values.
    

ComplianceOps
-------------

In the **ComplinaceOps** tab of the summary page, you will find the details of your assessment:

![](/tmpimg/2022-08-19_00-23-59.png)

In this tab, you have:

* **Lenses Summary —** In the lenses summary you have the option to add/remove the review lenses and the compliance frameworks. In this section, you will see the assessments and reports according to your selection, along with the _Assessment Completed_ percentage. If you change you selection, the assessments and reports will change accordingly. In this section you also have two buttons:
    
    * **Assessment —** Takes you to your assessment section.
        
    * **View Report —** Takes you to the assessment report page.
        
    
* **Top Recommendations —** Show you a list of top recommendation to resolve the violations.
    
* **Compliance Documents —** Show you the documents you attach to each recommendation in the **Top Recommendations** section.
    

## Running the Well-Architected Framework Review (WAFR) ##
====================================================

In this assessment section, you may notice that the assessment is at a completion percentage greater than 0%. This is because that nOps uses its rules engine to automatically discover information about the Workload and answers some the questions in the assessment:

![](/tmpimg/2022-08-19_01-20-00.png)

**Note:** Each question specifies whether this is considered a High, Medium or Low risk question.

The assessment questioner is divided in to the 6 pillars of the WAFR assessment. To switch to a specific assessment pillar, click on the desired pillar:

![](/tmpimg/2022-08-19_01-26-27.png)

Alongside the pillar name can also see how many question are answered and how many are still unanswered.

You can also click on the vulnerability levels to see exactly how many vulnerability are of the choose level:

![](/tmpimg/2022-08-19_02-07-20.png)

For _each_ question in the WAFR assessment, nOps will either automatically detect the answer to the question or allow you to answer it manually. Clicking on the checkbox(es) in each section will designate that your workload meets or exceeds the particular requirements. You can add notes to a particular question by clicking “**Add Note**.” Hover the mouse over a question to view a context menu that gives you several options.

* **Autodiscovery Details** \- Information about what nOps was able to detect in your account.
    
* **Attach Resources** \- Allows you to attach specific resources to a question. These resources will be included in the report generated by nOps.
    
* **Create Jira Ticket** \- If you have integrated an instance of Jira Cloud, you can open Jira issues from nOps. Use this option to assign tasks while completing your WAFR.
    
* **Show Description** \- Shows a description of the question.
    

To attach a Query to you answer as an evidence, click on the **\+ Attach Query**:

![](/tmpimg/2022-08-19_02-15-52.png)

You can also click on the _details_ icon to open a list of other options that you can use to enrich your answers:

![](/tmpimg/Cursor_and_nOps_Dashboard-4-2.png)

After you have answered each question, if you are working on this assessment for the first time, you can click **“Submit Report”**. This will enable you to export the report to AWS as part of the WAFR. Click **Export Report** for and select the desired export format.

Clicking **“Exit Assessment”** will return you to the summary screen where you can upload any additional documentation, see the assessment completion percentage, and export the report of the assessment.

## AWS Well-Architected Tool Integration ##
=====================================

While creating you Workload in nOps, if you selected "**Create workload on AWS account**", your Workload will be synchronized to the AWS Well-Architected Tool, each Workload in AWS will be listed as if you had created it from the tool itself.


Changes made from nOps can be synchronized to the AWS Well-Architected Tool by clicking **Update Report**.

## IAM Role Updates ##
================

If you are using an existing nOps account, you will receive notifications that nOps has added new AWS IAM policies to enable AWS Well-Architected Tool integration. Please update your IAM policies to allow nOps to access the AWS Well-Architected Tool in your account. For more information, you can watch this short video.

[Get notified about new AWS IAM policies on nOps - YouTube](https://www.youtube.com/watch?v=v5HG2eN3ifo)