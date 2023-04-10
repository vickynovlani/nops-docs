---
title: Foundational Technical Review
parent: FTR
grand_parent: User Guides
nav_order: 2
layout: default
---

{: .no_toc }
# Foundational Technical Review #
=============================


This article discusses:

- TOC
{:toc}

## Getting Started
---------------


For all AWS Partner-hosted solutions, passing the AWS Foundational Technical Review (FTR) requires you to complete an AWS Well-Architected Review (Review) to identify opportunities for improvement across all of the Well-Architected pillars.

You do not need to complete the remediation of identified issues to pass the FTR, only execute the Review. You can complete this assessment using either nOps or the AWS Well-Architected Tool accessible from the AWS Management Console.

_PREPARATION CHECKLIST:_ Before you begin, you will need to gather the following:

* Access to the master payer account if you are using organizations.
    
* Permission to create and run an AWS CloudFormation stack.
    
* Permission to create AWS Identity and Access Management (IAM) roles in your account.
    
* Friendly account name.
    
* The name of an Amazon S3 bucket where your AWS Cost and Usage Reports (CURs) will be written. (We will create one if one does not exist.)
    
* CURs are enabled in the account.
    

**_To Get started_** [Click Here](https://app.nops.io/accounts/ftr)

Signing Up for nOps
-------------------

**_Step 1:_** Once you’ve clicked on the link above ([nOps Sign Up](https://app.nops.io/accounts/ftr)), you’ll be taken to the FTR user registration page.

Complete the signup process by entering your business email, company name, etc. and clicking “Sign Up.” Doing so will cause a verification email to be sent to you — please click it to verify your email address. If you do not receive the verification email, please check your Spam folder.

[![](https://downloads.intercomcdn.com/i/o/286280604/e55780e3a4d271b80db6dbd4/image.png)](https://downloads.intercomcdn.com/i/o/286280604/e55780e3a4d271b80db6dbd4/image.png)

_Congrats! You are now registered as an nOps user._

Adding an AWS Account
---------------------

Connect your AWS account(s) where the resources in your workload live.

_*You will need to have access to the master payer account if you are using organizations. Additionally, you will need permissions to create and run a CloudFormation stack and create IAM roles in your account._

Click **_\+ Add AWS Account_** on the right.

Or, click on your username in the top right and go to: **_Settings_ \> _AWS Accounts_ Click _“Add a new AWS account.”_**

[![](https://downloads.intercomcdn.com/i/o/286280865/6a87c5bae619bde683b26180/image.png)](https://downloads.intercomcdn.com/i/o/286280865/6a87c5bae619bde683b26180/image.png)

_nOps has two setup options:_

* nOps Wizard Setup (recommended) - nOps will create a CloudFormation stack using your AWS credentials.
    
* Manual Setup - Used to reconfigure specific AWS accounts.
    

[![](https://downloads.intercomcdn.com/i/o/286280938/feb026bf2a381f9fea47be9b/image.png)](https://downloads.intercomcdn.com/i/o/286280938/feb026bf2a381f9fea47be9b/image.png)

When adding a new AWS account, nOps will ask for the friendly name and the name of an S3 bucket where your CURs will be written. If you already have an S3 bucket for your CURs, you can add it here. Otherwise, nOps will attempt to create an S3 bucket.

[![](https://downloads.intercomcdn.com/i/o/286281049/b9c23fc6a6f217a0767a99c1/image.png)](https://downloads.intercomcdn.com/i/o/286281049/b9c23fc6a6f217a0767a99c1/image.png)

Click **_“Setup Account”_** to be redirected to your AWS account.

_*Please remember to log in to the AWS account that you want nOps to collect data from._

Agree to the CloudFormation template being able to create an IAM role and then click _Create Stack._

**_Step 2_** Once you have successfully added your AWS account to nOps, it will start the data ingestion process.

[![](https://downloads.intercomcdn.com/i/o/286281209/0b239a9062644d6cf7a92ddf/image.png)](https://downloads.intercomcdn.com/i/o/286281209/0b239a9062644d6cf7a92ddf/image.png)

This process can take two to four hours, depending on the size of your AWS account. You should be able to see your AWS account in **_Settings_ \> _AWS Accounts_ \> _Active AWS Accounts_.**

**_AWS Accounts_** are now synced when this screen appears:

[![](https://downloads.intercomcdn.com/i/o/286281351/c5f1850d978faea83b726a1d/image.png)](https://downloads.intercomcdn.com/i/o/286281351/c5f1850d978faea83b726a1d/image.png)

Workloads
---------

A workload, in nOps, is a dynamic collection of AWS resources. Workloads allow you to group and manage only the resources that match a particular query. Click “Workloads” in the top nav bar to be taken to the Workloads view.

Creating Your First Workload
----------------------------

**_Step 3_** If this is the first time you have created a workload, you will be able to click “Create New Workload” in the middle of the screen. After that, the Create New Workload button will move to the top right of the window.

[![](https://downloads.intercomcdn.com/i/o/286281485/e632d0046228aa7fc546d9da/image.png)](https://downloads.intercomcdn.com/i/o/286281485/e632d0046228aa7fc546d9da/image.png)

When you click **_“Create New Workload,”_** the workload creation pane will slide into view.

* **Workload Name** \- This is the unique identifier for your workload.
    
* **AWS Account(s)** \- The AWS Account(s) where the resources for your workload live.
    
* **Workload Type** \- Defines the overall workload type. Please select “Well-Architected.”
    
* **Lens** \- nOps supports the AWS lens concept. Please select FTR for the lens type.
    
* **Environment** \- This defaults to Production and defines the environment from an AWS perspective.
    
* **Jira project** \- If you are using the built-in Jira integration, you will be able to select a Jira project to integrate with.
    
* **Description** \- A text description of your workload.
    

_*At this time, creating workloads in your AWS account is not fully functional. Clicking the option can cause errors in your workload creation._

Defining the Workload Query
---------------------------

**_Step 4_** After you have filled out the metadata for your workload, you can click the gray bar that says, **_“Specify Workload Resource,”_** causing the query builder to slide into view. nOps allows you to specify rules that define which resources will be added to the workload.

[![](https://downloads.intercomcdn.com/i/o/286281876/8c71b2bfb0429e91379c0834/image.png)](https://downloads.intercomcdn.com/i/o/286281876/8c71b2bfb0429e91379c0834/image.png)

* **Regions** \- The regions that nOps will pull resources from. This defaults to All.
    
* **AWS Managed Services** \- The AWS services that nOps will include in your workload. This defaults to All.
    
* **VPC** \- The VPCs that contain the resources that nOps will include in your workload. This defaults to All.
    
* **Tags** \- Select tags to be assigned to the resources you want to include, e.g., “ApplicationA.”
    

Click **_“Save”_** to create your workload.

Workload Summary View
---------------------

**_Step 5_** After you have created your workload, you will see the Workloads view. Here you can see a list of all workloads you’ve created, edit the query that builds your workload, and delete your workload.

[![](https://downloads.intercomcdn.com/i/o/286282109/506af50803db6c5f3407bb6f/image.png)](https://downloads.intercomcdn.com/i/o/286282109/506af50803db6c5f3407bb6f/image.png)

Click on the workload to be taken to the Workload Summary view. In the Workload Summary view, you will see two sections.

[![](https://downloads.intercomcdn.com/i/o/286282239/3cec7b7c8b883291c2828720/image.png)](https://downloads.intercomcdn.com/i/o/286282239/3cec7b7c8b883291c2828720/image.png)

**_Assessment Summary_** \- An overview of how far into the assessment you are. _\- Workload Attachments_ \- Any files and/or links attached to the workload are added to the report generated by nOps when the assessment is completed.

Running the FTR Assessment
--------------------------

You might notice that the assessment is at a completion percentage greater than 0. This is normal and due to the fact that nOps uses its rules engine to discover information about the workload automatically. Click _“Start Assessment”_ to begin the FTR Assessment.

[![](https://downloads.intercomcdn.com/i/o/286282463/07cfd400863550f1e801495f/image.png)](https://downloads.intercomcdn.com/i/o/286282463/07cfd400863550f1e801495f/image.png)

For each question in the FTR, nOps will either automatically detect the answer to the question or allow you to answer it manually. Clicking on the box(es) in each section will designate that your workload meets or exceeds the particular requirements. You can add notes to a particular question by clicking “Add Note.” Hovering the mouse over the question will raise a context menu that gives you several options.

* **Autodiscovery Details** \- Information about what nOps was able to detect in your account.
    
* **Attach Resources** \- Allows you to attach specific resources to a question. These resources will be included in the report generated by nOps.
    
* **Create Jira Ticket** \- If you have integrated an instance of Jira Cloud, you will be able to open Jira issues from nOps. Use this option to assign tasks while completing your FTR.
    
* **Show Description** \- Shows a description of the question.
    

After you have answered the question, you can click _“Submit Report,”_ enabling you to export the report to AWS as part of the FTR. Clicking _“Exit Assessment”_ will return you to the summary screen where you can upload any additional documentation, see the assessment completion percentage, and export the report of the assessment.

Submitting the Package to AWS
-----------------------------

**_Step 6_** Once you have completed the FTR Assessment, you will need to export your completed FTR Report and send it to your Partner Solutions Architect via email. You will also need to include the following information:

* A brief description of your solution.
    
* An architecture diagram illustrating major system components and their network communication paths (examples of reference architecture diagrams here).
    
* Is the solution currently generally available to customers?
    
* Is the solution in AWS GovCloud? If yes, what is the reason it is in AWS GovCloud?
    

Next Steps
----------

nOps enables you to complete your FTR efficiently, but it can do far more than that. nOps lets you monitor, analyze, and manage an AWS Well-Architected infrastructure that is cost-optimized, secure, reliable, efficient, and operationally excellent — and help keep it that way through continuous compliance.

[Click here](https://www.nops.io/resources/brochures-and-videos) to learn all you can do with nOps.