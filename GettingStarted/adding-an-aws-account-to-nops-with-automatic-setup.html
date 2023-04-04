# Adding an AWS account to nOps with Automatic Setup #
--------------------------------------------------

## Setting up an AWS nOps account (Automatic Setup) ##

nOps requires safe, secure, and AWS-approved access to your AWS accounts in order to give you the analysis, dashboards, and reports that you need. We only see what we need, no more, and we need you to give us permission first.

In order to get started with nOps, the first step is to set up an AWS account for nOps via the Setup Wizard and subscribe to nOps on the AWS marketplace. We made the setup process as easy as possible for you while complying with AWS security best practices.

In Automatic Setup, nOps takes care of creating the IAM policy and the CloudFormation stack for the account.



## Prerequisites
To successfully set up the AWS account(s), the AWS user must possess:

* Access to the Payer account, if you are using AWS Organizations.
* Permission to create and run an AWS CloudFormation stack.
* Permission to create AWS Identity and Access Management (IAM) roles in your account.
* The name of an Amazon S3 bucket where your AWS Cost and Usage Reports (CURs) will be written. (nOps will create a bucket with the provided name if one does not exist.)
* CURs enabled in the account.

* * *

**Note:** If you add an AWS child account instead of a Payer Account, nOps will only see the cost details of the specific child account instead of the cost details of the entire organization.

* * *

Adding AWS Account(s)
---------------------

When you log in to your nOps account for the first time, a pop-up screen will appear. This pop-up screen will guide you on how you can add your AWS account(s) to nOps. The screen consists of four distinct sections:

1.  [Select Cloud Type](#h_910dd1dd7c)
2.  [Getting Started](#h_b839a84580)
3.  [Link Cloud Accounts](#h_86e3a87963)
4.  [Fetching](#h_43a0c3160f)

* * *

**Note:**

If you only add a single account during the automatic setup and want to add more accounts later, once your single account is onboarded and you have access to the nOps platform:

1.  On the top-right corner of your nOps account, click on your user avatar to open a drop-down list.
2.  In the dropdown list, click **Organization Settings**. This will take you to the **Cloud Accounts** page.
3.  On the **Cloud Accounts** page, click **\+ Add New Account**.

* * *

Select Cloud Type
-----------------

On this page, select the type of cloud account that you want to onboard and click **Next**. In the scope of this document, we will only explore the **AWS Account** option.

If you want to explore nOps first before you onboard any accounts, click **Let Me Explore App**.

Getting Started
---------------

In this section, you need to select the account setup method. In the scope of this article, we will deal with the **Automatic Setup**. Select the **nOps Wizard Setup** and click **Next**.

* * *

To learn more about **Manual Setup**, see [Manual Setup](https://help.nops.io/en/adding-an-aws-account-to-nops-with-manual-setup/). To learn more about **IaaC Setup**, see **IaaC Multiple Accounts Setup**.

* * *

Link Cloud Accounts
-------------------

On the first page of this section, you can either select an AWS _Organization_ account or a _Single Account_.

In the case of an **AWS Organization** account:

* Make sure that you are logged into your AWS Master Payer Account.
* Select the _AWS Organization_ option.
* Fill out the _AWS Master Payer Account Name_ and _S3 Bucket Name_ fields.
* Click **Setup Account.**

If you select **AWS Organization** account, in the next section **Link Cloud Account**, you will have the option to onboard the child accounts associated with your _AWS Organization Account_.

In the case of **Single Account**:

* Make sure that you are logged into your AWS account.
* Select the _Single Account_ option.
* Fill out the _AWS Account Name_ and _S3 Bucket Name_ fields.
* Click **Setup Account.**

When you click **Setup Account**, you will be redirected to your **AWS** \> **Create Stack** page. All the fields on this page will be pre-populated. Click on the checkbox for **“I acknowledge that AWS CloudFormation might create IAM resources”**. nOps needs this permission to automate the creation of the IAM role.

After you click the checkbox, click on the **Create** button to start the data ingestion.

* * *

**Note:**

CF stack can run from any region you prefer. You can easily change the region of the CF stack from the **CloudFormation** screen once you launch it from nOps after your setup process is complete.

* * *

Once the stack is created, come back to nOps. nOps will check the account connectivity with AWS and check the CloudFormation stack permissions, and start the ingestion:

When data ingestion starts, in AWS console **CloudFormation > Stacks > Stack Detail**:

1.  If you have all the required permissions, as mentioned in the prerequisites section, the setup will start creating the stack with the status **“CREATE\_IN\_PROGRESS”**. Once the stack is created the **“Status”** will change to **“CREATE_COMPLETE”**. You can click the browser refresh button to check progress. Normally it takes 1 to 2 minutes to complete the process.
2.  If you don’t have proper permissions then you will see errors as shown in the screenshot below, and the stack will not be created. You can assign the necessary permissions to the AWS user or ask other teammates to rerun the setup.
3.  Once the stack creation is successful, log in to [nOps Dashboard](https://app.nops.io/) after the nOps integration (stack) creation process is completed

Fetching
--------

Once your AWS accounts are linked successfully, you will see the following screen:

![](https://help.nops.io/wp-content/uploads/2023/03/fatcing-1024x694.jpg)

Once you log back into nOps, after data ingestion is complete, in the case of AWS _Organization Account_ you will see the **Setup Child Account** page. With the help of your CUR, the setup process will automatically pull in the child accounts associated with your organization account.

To onboard a child account, click the **Automatic Setup** button against the child account that you want to add. If you don’t want to add a specific child account, click **Skip Setup.**

* * *

**Note:**

If you don’t have the required permissions to onboard a child account, click **Invite team member** to invite a member of your organization who has the required permissions.

* * *

If you click **Automatic Setup**, the setup process will show you a confirmation popup.

Before you click **Proceed**, make sure that you are logged in to the child account you are onboarding. When you click **Proceed,** you will be redirected to the AWS CloudFormation console with all the fields pre-filled:

![](https://help.nops.io/wp-content/uploads/2023/03/Quick-create-stuck-Automatic-Setup-905x1024.jpg)

Check the **I acknowledge that AWS CloudFormation might create an IAM resources** checkbox, and click **Create Stack**.

To take a look at the nOps CloudFormation template, see [CloudFormation YAML Template](https://s3-us-west-2.amazonaws.com/nops-users/nOpsRole-uat.yaml).

In case, nOps detects more than 10 child accounts, you will get a prompt to use the [nOps IaaC Setup](https://help.nops.io/en/adding-aws-accounts-to-nops-with-terraform/). nOps recommends that in this case, you use the IaaC Setup instead of the **Automatic Setup**. To learn more about the IaaC setup, see **IaaC Multiple Account Setup**.

Once all the Child Accounts are added or skipped, click **Next.**

The setup process is now complete.

* * *

**Note:**

It can take up to 24 hours before you start seeing the different nOps dashboards and compliance views populated with data from your workload.

* * *

If you have any questions, please contact us at [help@nops.io](mailto:help@nops.io), or by phone at +1 866-673-9330.

On initial ingestion, nOps will pull the data from AWS accounts based on the following durations:

* Cost data: 6 months look back + current month.
* Rules: Current date.
* CloudTrail Events: 14 days look back.

IAM and CloudFormation:
-----------------------

The IAM policy used by nOps is scoped to read and write permissions only.

Lambda function automates the creation of Role and Bucket (if it’s absent) for nOps integration to work.

The code for the Lambda function is available for your review. Click the link to get the [YAML file](https://s3-us-west-2.amazonaws.com/nops-users/nOpsRole-uat.yaml).

If you are not comfortable with using the automated setup, you can use manual steps for the setup.

Article: [Adding Your AWS account with the Manual Setup](https://help.nops.io/en/adding-an-aws-account-to-nops-with-manual-setup/)

![](https://help.nops.io/wp-content/uploads/2023/03/IAM-and-CloudFormation.jpg)

_View the latest [IAM Policy here](https://app.nops.io/c/aws/policy/get_iam_policy/)_

Troubleshooting Tips:
---------------------

* Do you have a **pop-up blocker** on your browser? A pop-up blocker on your browser will stop nOps from redirecting you to an AWS account to create a stack.
* There may have been a disconnect when creating the S3 stack causing the stack to have an error of **ROLLBACK_ERROR.** In this case, re-try the automatic setup, then delete the first one.
* Is it pulling in incorrect data? Make sure that you are logging into the correct account. When you have multiple access to AWS accounts, it can import the wrong data. Ensure that you’re logged in to the correct account prior to starting the integration process.
* If you belong to an Organization ( multiple accounts linked to a Master Account) ensure that you are logged into the Master account before running the wizard (so the billing data is populated) or having organizational billing data files exported to one of your buckets.

Related Articles:

[How Child Accounts Work in nOps](https://help.nops.io/en/adding-aws-child-accounts-in-nops/)
