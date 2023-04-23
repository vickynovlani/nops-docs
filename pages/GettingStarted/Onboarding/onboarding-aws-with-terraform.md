---
title: Onboarding AWS Accounts to nOps with Terraform
keywords: setup, onboarding, terraform
tags: [getting_started, onboarding]
sidebar: mydoc_sidebar
permalink: onboarding-aws-with-terraform.html
folder: GettingStarted
---

# Adding AWS Account(s) to nOps with Terraform #

## Onboarding via IaaC (Terraform) ##

nOps requires safe, secure, and AWS-approved access to your AWS accounts in order to give you the analysis, dashboards, and reports that you need. We only see what you want us to see in order to provide our services, no more, and we need you to give us permission first.

In order to credential and register multiple accounts, we leverage _AWS Organizations_, _CloudFormation_, _StackSets_, and _Lambda_.

**Prerequisites**

* Admin role permissions in AWS in order to add AWS Payer and/or Child accounts to nOps using _Terraform_.
    
* Access to the nOps public Github repository [nOps Cloud Account Registration](https://github.com/nops-io/nops-cloud-account-registration).
    

## nOps Onboarding - Terraform Setup ##

When you log in to your nOps account for the first time, a pop-up screen will appear. This pop-up screen will guide you on how you can add your AWS account(s) to nOps. The screen consists of four distinct sections:

1.  [Select Cloud Type](#cloudtype)
    
2.  [Setup Method](#setupmethod)
    
3.  [Link Cloud Accounts](#linkaccounts)
    
4.  [Fetching](#fetching)
    

### 1 - Select Cloud Type ### {#cloudtype}


On this page, select the type of cloud account that you want to onboard (AWS or Azure) and click **Next**.

In the scope of this article, we are going to deal with the **AWS Account** setup process.

### 2 - Setup Method ### {#setupmethod}


In this section, you need to select the account setup method. In the scope of this article, we will deal with the **IaaC Multiple Accounts Setup**. Select the **IaaC Multiple Accounts Setup** option and click **Next**.

### 3 - Link Cloud Accounts ### {#linkaccounts}


The first page in the Link **Cloud Accounts** section informs you of the prerequisites. If this is your first time onboarding accounts in nOps, click **Proceed to Create API Key**.

* * *

On the second page in the **Link Cloud Accounts** section, enter:

* An API key name
    
* API Key description
    
* Signature verification (optional)
    

After you add all the information, click **Create API Key.**

Once you click **Create API Key** nOps will generate an API key for you. Copy and save the API key for future use, and click **Next**.

When you click **Next**, nOps will start checking for its connectivity with your AWS accounts. In order for nOps to establish a connection with your accounts and start fetching data, you need to:

1.  Go to your AWS console to enable **CloudFormation Stacksets** in **AWS Organization**, and enable **StackSets** in **AWS CloudFormation**.
    
2.  Go to the [nOps Cloud Account Registration](https://github.com/nops-io/nops-cloud-account-registration) Github repo and follow the instructions in **Terraform Multiple Child Account Registration via Stackset** section.
    

To enable **CloudFormation StackSets** in _AWS Organizations_, go to **AWS Organizations > Services**. If you see **Access disabled** against **CloudFormation StackSets** option, enable it.

To enable **StackSets** in **AWS CloudFormation**, go to **CloudFormation > StackSets**. If there is no prompt to enable **StackSets**, then skip this step. If you see an option to enable the **StackSets**, then enable it.

Before you continue with the onboarding process any further, make sure that you have:

* nOps API Key
    
* IDs of Organization Units you want to onboard.
    
* Organization Root ID.
    
* Payer Account ID.
    

* * *

**Note:**

To view the details about your organization including Organization Unit IDs, Root ID, and Master Payer Account ID, see [Details About Your Organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_details.html#orgs_view_ou).

* * *

nOps Terraform code is available in a public GitHub repository [nOps Cloud Account Registration](https://github.com/nops-io/nops-cloud-account-registration). You need to:

1.  Clone the repository.
    
2.  Navigate to \`nops-cloud-account-registration/nops-aws-account-register/\`.
    
3.  Follow the instructions in [`terraform-master-payer-regiaster/`](https://github.com/nops-io/nops-cloud-account-registration/tree/main/nops-aws-account-register/terraform-master-payer-register) folder to add a Payer account. Follow the instruction in [`terraform-multiple-child-accs-register-via-stacksets/`](https://github.com/nops-io/nops-cloud-account-registration/tree/main/nops-aws-account-register/terraform-multiple-child-accs-register-via-stacksets) folder to add child account(s).
    

After you've gone through the installation steps in the public GitHub repository ([nOps Cloud Account Registration](https://github.com/nops-io/nops-cloud-account-registration)), the data ingestion process will start.

You can monitor the progress from the terminal where you ran the Terraform commands or you can also monitor the progress from the [AWS CloudFormation console](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacksets). In your **AWS CloudFormation** console, find the stack with the name **member-consolidated-nops-account-register**, open it, and go to the **Stack Instances** tab to see the progress.

After a few minutes (depending on the number of accounts) all stacks should be in the state **CURRENT**.

### 4 - Fetching ### {#fetching}


Once your AWS accounts are linked successfully, the data-fetching process will start It might take several hours for nOps to fetch the data from your AWS account, in the meantime, you can click **Let Me Explore** to enter the nOps web application to see all the savings that nOps has to offer.  
  
When the data fetching process is complete, you will see the message **Your AWS accounts linked successfully** on the setup screen.

The setup process is now complete and you will see the following screen.

If you have any questions, please contact us at [help@nops.io](mailto:help@nops.io).

On initial ingestion, nOps will pull the data from AWS accounts based on the following durations:

* **Cost data:** 6 months look back + current month.
    
* **Rules:** Current date.
    
* **CloudTrail Events:** 14 days look back.