---
title: Setting up an AWS nOps account with Manual Setup
parent: Onboarding
grand_parent: Getting Started
nav_order: 3
layout: default
---

# Setting up an AWS nOps account (Manual Setup) #

nOps requires safe, secure, and AWS-approved access to your AWS accounts in order to give you the analysis, dashboards, and reports that you need. We only see what you want us to see in order to provide our services, no more, and we need you to give us permission first.

In order to get started with nOps, the first step is to set up an AWS account for nOps via the [Automatic Setup](https://help.nops.io/en/adding-an-aws-account-to-nops-with-automatic-setup/), Manual Setup, IaaC Multi Account Setup (CloudFormation), or IaaC Multi Account Setup (Terraform). We made the setup process as easy as possible for you while complying with AWS security best practices.

This Manual Setup is used in complex environments by experienced AWS administrators who need granular control and insight into the access that nOps require.

The Manual Setup approach is also useful for administrators who want to embed nOps access into their automation.

Prerequisites
-------------

You must have Admin role permissions in AWS before you can set up an AWS nOps account with Manual Setup.

**Pro Tip:** The Manual Setup is used in complex environments by experienced AWS administrators. Most customers opt to use the Automatic Setup procedure.

Adding AWS account (Manual Setup)
---------------------------------

In the scope of this article, we will look at the Manual Setup procedure.

To use the Manual Setup for complex environments, follow these steps, in this order:

1.  [Get the auto-generated External ID from nOps](#h_e45f2f70f8)
2.  [Setup a S3 billing bucket for Cost & Usage Reports](#h_c4e39aec8e)
3.  [Give nOps Permission and Create an IAM Policy](#h_46c669eff1)
4.  [Create an IAM Role](#h_a4f27068c8)
5.  [Return to nOps to complete Manual Setup](#h_b387de537f)

**Note:** If you need any help with this process don’t hesitate to contact [help@nops.io](mailto:help@nops.io)

### Important information to copy and save

During this process, you should copy and save some information as you will need to enter it later. This information will be used in AWS and in nOps in order to complete the process:

* Copy the **External ID** auto-generated through nOps.
* Copy the **ARN** for **IAM Policy** that was created in the IAM Policy.
* Copy **Report name** created for the Cost and Usage Report (CUR).
* Copy **Report path prefix** from the S3 billing bucket creation.

Get the auto-generated External ID in nOps
------------------------------------------

When you log in to your nOps account for the first time, a pop-up screen will appear. This pop-up screen will guide you on how you can add your AWS account(s) to nOps. The screen consists of four distinct sections:

1.  Select Cloud Type
2.  Getting Started
3.  Link Cloud Accounts
4.  Fetching

If you only add a single account during the automatic setup and want to add more accounts later, once your single account is onboarded and you have access to the nOps platform:

1.  On the top-right corner of your nOps account, click on your user avatar to open a drop-down list.
2.  In the dropdown list, click **Organization Settings**. This will take you to the **Cloud Accounts** page.
3.  On the **Cloud Accounts** page, click **\+ Add New Account**.

### Select Cloud Type

On this page, select the type of cloud account that you want to onboard and click **Next**.

In the scope of this article, we are only going to deal with the **AWS Account** setup.

## Getting Started ##
---------------

In this section, you need to select the account setup method. In the scope of this article, we will deal with the **Manual Setup**. Select the **Manual Setup** and click **Next**.

When you click **Next,** you should see a screen similar to:

![](https://help.nops.io/wp-content/uploads/2023/03/mvv-1024x641.jpg)

Copy the **External ID** and save it, you will need it later on.

If you want to add more accounts after the completion of your onboarding:

1.  Log into the nOps application.
2.  From your **Profile** name drop-down, in the top-right, click **Organization Settings**. If you are a Partner or Client Admin, select a client first, then click **Organization Settings.**
3.  In the Settings page, click **\+ Add New Account**, this will take you to the **Cloud Account** page.
4.  In the **Cloud Account** page, select **AWS Account** and click **Next**. This will take you to the **Setup Method** page.
5.  In the **Setup Method** page, select **Manual Setup** and click **Next.** This will take you to the **Account Details (Manual Setup)** page.
6.  In the **Account Details (Manual Setup)** page, an **External ID** is auto-generated for you and prefilled in the External ID field.

**Important:** Do not exit this page, you will return to this page later to complete the account setup.

## Setup S3 billing bucket for Cost & Usage Reports ##
------------------------------------------------

This section is divided into two steps, in the first step you will create the Cost & Usage Report, and in the second step you will create/select an S3 bucket for the Cost & Usage Report.

**Note:** Ensure that your AWS SCP configurations allow IAM administrators to make the changes.

## Create the Cost & Usage Report ##
------------------------------

In this step you will create a Cost & Usage Report (also called Detailed Billing Reports or CUR) so that nOps can analyze your cost information:

1.  Login to your AWS Management Console account.
2.  Go to: **Billing & Cost Management Dashboard  
    **On the left-hand side select **Cost & Usage Report  
    **or, go to: [https://console.aws.amazon.com/billing/home?#/reports](https://console.aws.amazon.com/billing/home?#/reports)
3.  Click on C**reate Report:**[](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/536738226/eecaa2fcab4c7a904f63794b/dKBXmmqE2k-hr8pVWyI9OFY1qR50B9MWhHkXABU9NnbHl-c0QVDBsCK1x9ZfEdjlIFKIzlzn6WqlsKSjz2NuBKHJPscLRme2ZBRNU5zqyKRqlD1OH2XOGFYTZCe7xzPeNkp-StCfkYvucEYNLw)
4.  Create a **report name** (such as_nopsbilling-daily-gzip)._
5.  In **Additional report details,** check the **Include resource IDs** checkbox (mandatory).
6.  In the **Data refresh settings,** checkthe **Automatically refresh your Cost & Usage Report when charges are detected for previous months with closed bills** checkbox.
7.  Click **Next**.

When you click **Next,** it will take you to the **Delivery options** page where you will create the S3 billing bucket.

## Create/Select the S3 billing bucket ##
-----------------------------------

AWS needs a place to save your cost and usage/detailed billing files, a place that is safe for you. In this step, you will create an S3 bucket that secures your information:

1.  In the **Delivery options** (the page you reached at the end of the last section), click **Configure.** This will open the **Configure S3 Bucket** dialog box.
2.  In the dialog box, do one of the following:  
    **– Select an existing bucket**: Use an existing bucket from your AWS Account.  
    or  
    **– Create a new bucket:** Create a new S3 bucket to be used specifically for nOps.[](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/536738235/595ec97964c11d9605706de3/Fd3QddzVrnAB0658rGviIMbNR0SJRc5015vaOQAa7VgT90M8PG5g4r9XTbuadkWlu_P3LHEivuN9yWb0pBxqfKbiTfxOy5753TmPXkaKJYtTPT8ZZH7WbHswxlDDtNpWtfds1JhINPGaxN6LJg)
3.  Click **Next** to go to **Verify Policy.**
4.  Check the **“I have confirmed that this policy is correct”** checkbox.
5.  Click **Save** to save this policy**.** When the policy is saved, you will return to the **Delivery options** page.
6.  In the **Delivery options** page:  
    [](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/536738239/f79a9fb24ce381cb68555cd2/z8P2UxECPgnyM4gC4XddG6cLH8f2CN79rQEoDfaSHa70D98QJHeBkHj9cb4-_gS7oysTlAMa3VDuEZ47DFF4e2uPYACFixVhxnYYOk027DUhLhIfXdO_T0pLetZMIebDawsOclf702fyEFOp9w)
    * **Click** the **Verify** button to make sure the S3 bucket has an appropriate policy for the delivery report (step 3).
    * Enter the **report path prefix** (required) – Suggestion: _nopsbilling_
    * Choose **Daily** (mandatory) for **Time granularity.**
    * Select an option for **Report versioning** (optional) — Suggestion: Overwrite existing report.
    * Select **GZIP** as **Compression type** (mandatory).  
        **Important:** You will need the **Report Path Prefix name** later when you are adding the AWS Account in nOps

7\. Click **Next.**

8\. Then, click **Review and Complete.**

Give nOps permission: Create the IAM policy
-------------------------------------------

In this step, you’ll give nOps permission to read the Cost & Usage Report in the S3 bucket.

**Note:**

———-

AWS has a sophisticated security system for Identity and Access Management (IAM). There are no shortcuts for this. The nOps [Wizard/Automatic Setup](https://help.nops.io/en/adding-an-aws-account-to-nops-with-automatic-setup/) makes this easier with a CloudFormation Template, but the details provided in this article are for AWS practitioners who need more information for their own automation or auditing purposes.

———-

To manually create the IAM policy in order to allow nOps access:

1.  On the AWS Management Console, go to the **Identity and Access Management** screen.
2.  From the left navigation panel, click **Policies.**
3.  Click **Create Policy**.
4.  Switch to the **‘JSON’** tabandreplace the existing JSON script with the script provided in [nOps IAM Policy](https://help.nops.io/en/aws-iam-policy-nops-free-platform/) (click this link to get the script).
5.  Click **Next: Tags** (optional)**.**
6.  Click **Next: Review.**
7.  Click on **‘Review Policy’**.
8.  **Copy and save the ARN of the IAM role.** This will be used later when you create the **IAM Policy**.
9.  Provide a name and description for the policy.
10. Click on ‘**Create Policy**’.

Now, follow the same steps above to create another policy, this time for the S3 bucket that houses the Cost & Usage Report.

To create this policy, follow all the steps as is except for step 4. In step 4 use the following script:

    {"Version": "2012-10-17","Statement": [{"Action": "s3:*","Effect": "Allow","Resource": ["arn:aws:s3:::<paste-bucket-name-here>","arn:aws:s3:::<paste-bucket-name-here>/*"]}]}

Make sure you replace &lt;paste-bucket-name-here&gt; with the name of the S3 bucket that houses the Cost & Usage Report to ensure policy efficacy.

You will attach both above policies to the IAM Role that you will create for nOps in the next step.

Creating IAM roles
------------------

**IMPORTANT:** You will need to enter the [nOps auto-generated ID](#h_e45f2f70f8) to create the IAM Role.

In order to allow the nOps SaaS application to use the IAM policy you just created, you need to create an IAM role.

To create a new role:

1.  On the AWS Management Console, go to the **Identity and Access Management** screen.
2.  From the left navigation panel, click **Roles.**
3.  Click **Create Role.**
4.  On **Select trusted entity** page, select **AWS account.**
5.  Click **Another AWS account.**
6.  For **Account ID** enter the nOps account ID (202279780353).[](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/536738257/9c1c309f57de267c086653ad/MQQ1lztKqgg6xsfoZRG_-Qxgg6Leervp_RUMC-_ojV1DQPme3lJS1jWqp_5vJnaWSxl-03dw6D4GqG9grBl99OVL09RpN2zQ5Ycxn0DLJlWCVzpdOBB5Jkg1ZqaaglSAwjzZP1pc4xHuLGhK8w)
7.  Click **Require external ID**.
8.  For **External ID**, enter the string that was auto-generated for you by nOps in [Step](#h_e45f2f70f8). The auto-generated **External ID** adds an extra level of security for you.
9.  Click **Next.**
10. In **Add permissions**, select the two IAM policies you created in [Give nOps permission: Create the IAM policy](#h_46c669eff1).
11. Click **Next**.
12. Enter a name and description for the role.
13. Click **Add tags,** in orderto add tags to be associated with this role (optional).
14. Click **Create Role.**

You have now completed the first part of the Manual Setup related to the AWS console.

Continue the Manual Setup of AWS account in nOps
------------------------------------------------

Now that you have manually configured an IAM Role in your AWS account for access to AWS resources, the last step is to add that account to nOps.

Since you have already generated an **External ID** for nOps in [Create an auto-generated External ID from nOps](#h_e45f2f70f8), you must now add information about the AWS role you created for nOps to fetch CloudTrail. You also need to add the S3 bucket so that nOps can fetch the billing data including the Cost & Usage Report.

**Note:** If you do not add a S3 bucket, your billing stats pages in nOps will not display any data.

1.  Start from where you left off in [Create an auto-generated External ID from nOps](#h_e45f2f70f8) section.
2.  In the **Account Details (Manual Setup)** page**,** enter a name for the AWS account you are adding to nOps.
3.  The External ID is auto-generated.
4.  Enter the ARN of the IAM role that you copied earlier in step 8 of **Give nOps permission: Create the IAM policy** section.
5.  Add the S3 bucket name. Make sure the S3 bucket name is the **_same_** as the S3 bucket you created for **Cost & Usage Report** in the AWS console.
6.  Enter the name of the Cost & Usage Report you created in step 4 of [Create the Cost & Usage Report](#h_ec22fd4d8d) section.
7.  Enter the report prefix path that you created in step 6 of [Create/Select the S3 billing bucket](#h_3cf7f8c7ac).
8.  Click **Setup Account**.

![](https://help.nops.io/wp-content/uploads/2023/03/a-1024x641.jpg)

When adding the AWS account to nOps make sure you save the settings after filling all the fields.

Link Cloud Accounts
-------------------

nOps will check the account connectivity with AWS, and start the ingestion:

![](https://help.nops.io/wp-content/uploads/2023/03/linking-aws-account-1024x595.jpg)

Fetching
--------

Once your AWS accounts are linked successfully, you will see the following screen:

![](https://help.nops.io/wp-content/uploads/2023/03/aws-master.jpg)

Once you log back into nOps, after data ingestion is complete, in the case of AWS _Organization Account_ you will see the **Setup Child Account** page. With the help of your CUR, the setup process will automatically pull in the child accounts associated with your Organization account:

![](https://help.nops.io/wp-content/uploads/2023/03/2brJ8KFahYnFiuiAlTgbfeyoyiZ_vIXPxpIa-7neWsCHiP_-3BGKOr1R5b084TbCsMRRgBHMRqcXrWObzoUvkn1jcmcSrYCnNV9BVNSA0nqwEEdGP90Xwm7EX5j6k732fTo3BzTLZqxTBULkWbq0TI5N6qFY95P7iVjU4Jmd7gcs5jyH9SZBec2zmg.jpg)

To onboard a child account, click **Automatic Setup**. If you don’t want to add a specific child account, click **Skip Setup**

If you don’t have the required permissions to onboard a child account, click **Invite team member** to invite a member of your organization who has the required permissions.

If you click **Automatic Setup**, the setup process will show you a confirmation popup:

![](https://help.nops.io/wp-content/uploads/2023/03/Automation-setup.jpg)

Before you click **Proceed**, make sure that you are logged in to the child account you are onboarding. When you click **Proceed,** you will redirect you to the AWS CloudFormation console with all the fields pre-filled:

![](https://help.nops.io/wp-content/uploads/2023/03/Quick-create-task-905x1024.jpg)

Check the **I acknowledge that AWS CloudFormation might create an IAM resources** checkbox, and click **Create Stack**.

To take a look at the nOps CloudFormation template, see [CloudFormation YAML Template](https://s3-us-west-2.amazonaws.com/nops-users/nOpsRole-uat.yaml).

If you decide not to give nOps the required access, you might face the following warning:

![](https://help.nops.io/wp-content/uploads/2023/03/aws-master-payer-cloud-account.jpg)

You can click **Proceed and Setup later**, but in this case you will not be able to access the features that depend on the required services.

In case, nOps detects more than 10 child accounts, you will see the following prompt:

![](https://help.nops.io/wp-content/uploads/2023/03/master-payer-account-linked.jpg)

nOps recommends that in this case, you use the IaaC Setup instead of the **Automatic Setup**. To learn more about the IaaC setup, see **IaaC Multiple Account Setup**.

Once all the Child Accounts are added or skipped, click **Next.**

The setup process is now complete:

Note: It can take up to 24 hours before you start seeing the different nOps dashboards and compliance views populated with data from your workload.

If you have any questions, please contact us at [help@nops.io](mailto:help@nops.io), or by phone at +1 866-673-9330.

On initial ingestion, nOps will pull the data from AWS accounts based on the following durations:

* Cost data: 6 months look back + current month.
* Rules: Current date.
* CloudTrail Events: 14 days look back.

The Manual Setup is now complete.

**Note:** It can take up to 24 hours for data to populate. If you have any questions, please contact us at [help@nops.io](mailto:help@nops.io)

**Viewing Added AWS Accounts:**
-------------------------------

In nOps, you can view the list of all cloud accounts that you add to nOps.

To view the cloud accounts, go to **UserName Dropdown (Top right) > Organization Settings > Cloud Accounts** where:

* For AWS accounts, the name of the S3 bucket \[If added\] is displayed, and also the “Last fetch” time of the S3 bucket.
* For Azure accounts, the name of the account is displayed.

To edit an existing cloud account:

* Go to **UserName Dropdown (Top right) > Organization Settings > Cloud Accounts**
* Click the **Edit** button.

You can make any changes you need. Ensure that, when you are done making the changes, you click the **Update Account** button in order to save the changes.

**Note:** Editing the S3 bucket, for an AWS account, of an _existing_ project can cause changes in cost data or undesired results.

Related Articles:

[How Child Accounts Work in nOps](https://help.nops.io/en/adding-aws-child-accounts-in-nops/)

[How to Add a Read Only IAM Policy](/GettingStarted/aws-iam-policy-nops-free-platform.md)