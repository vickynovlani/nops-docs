---
title: Adding Multiple AWS Account to nOps with CloudFormation
parent: Getting Started with nOps
nav_order: 6
layout: default
---

## Adding Multiple AWS Account to nOps with CloudFormation ##

nOps requires safe, secure, and AWS-approved access to your AWS accounts in order to give you the analysis, dashboards, and reports that you need. We only see what you want us to see in order to provide our services, no more, and we need you to give us permission first.

In order to credential and register multiple accounts, we leverage _AWS Organizations_, _CloudFormation_, _Stack_, _StackSets_, and _Lambda_.

For multi-account setup, nOps recommends that use CloudFormation (this setup) instead of Terraform (intended for advanced users with specific requirements).

In this CloudFormation setup, the S3 bucket with the CUR is only required with the Master Payer account.

For a Master Payer account or a single account, during this setup, you will use the same CloudFormation YAML template for both. In order to add Child accounts, you will use a different CloudFormation template. Thus, you will create two stacks, one for the Master Payer, and one for the Child accounts.

Prerequisites
=============

*   You must have Admin role permissions in AWS before you can add multiple AWS accounts to nOps using _CloudFormation_.
    
*   Access to the nOps public Github repository [nOps Cloud Account Registration](https://github.com/nops-io/nops-cloud-account-registration).
    

Once you’ve taken care of the prerequisites, the next steps are simple and straightforward.

Adding Multiple AWS Accounts (CloudFormation)
=============================================

When you log in to your nOps account for the first time, a pop-up screen will appear. This pop-up screen will guide you on how you can add your AWS account(s) to nOps. The screen consists of four distinct sections:

1.  Select Cloud Type
    
2.  Getting Started
    
3.  Link Cloud Accounts
    
4.  Fetching
    

After the **Link Cloud Accounts** section, in the case of _Adding Multiple AWS Accounts (CloudFormation),_ you need to perform these extra steps on the AWS console:

1.  Enable _Stackset_ in _AWS Organizations_ and _AWS CloudFormation_.
    
2.  Go to AWS CloudFormation and create a Stack for the Master Payer account.
    
3.  Log in to the Master Payer account and create a Stackset for the child/member accounts.
    

To create the Master Payer account Stack and the child/member account stacksets, use the CloudFormation YAML templates from [nOps Cloud Account Registration](https://github.com/nops-io/nops-cloud-account-registration) public GitHub repository.

Pull the [nOps Cloud Account Registration](https://github.com/nops-io/nops-cloud-account-registration) public repository to your local machine before you continue with the setup. You will need the CloudFormation YAML templates in the repository while creating the stacksets. You will also need the nOps API key.

Select Cloud Type
-----------------

On this page, select the type of cloud account that you want to onboard and click **Next**.

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694160/bcf1f1ee6aefb65e47bb6a7d/FZFS_appbqgrryqAKcw17CpB_CKGVhr2fdzcm1N_B5v7w_Rtg0IIKwlIoG7sW_L6uMJ8uPbl-qkzKZPd2x5tqfz_iV1Z_2M5ksQgb_PgFe93X1k4nELjWHraRFolQbvR6EqlXUlElvSdIrCZXPNtBYBDx5v3Js11O9Bu4_FxPVTAaIa1oL6KiJwtJg)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694160/bcf1f1ee6aefb65e47bb6a7d/FZFS_appbqgrryqAKcw17CpB_CKGVhr2fdzcm1N_B5v7w_Rtg0IIKwlIoG7sW_L6uMJ8uPbl-qkzKZPd2x5tqfz_iV1Z_2M5ksQgb_PgFe93X1k4nELjWHraRFolQbvR6EqlXUlElvSdIrCZXPNtBYBDx5v3Js11O9Bu4_FxPVTAaIa1oL6KiJwtJg)

In the scope of this article, we are going to deal with the **AWS Account** setup process.

Getting Started
---------------

In this section, you need to select the account setup method. In the scope of this article, we will deal with the **IaaC Multiple Accounts Setup**. Select the **IaaC Multiple Accounts Setup** option and click **Next**.

Link Cloud Accounts
-------------------

The first page in the Link **Cloud Accounts** section informs you of the prerequisites. If you are adding multiple accounts after you’ve already been onboarded into nOps, go to [Create an API key](https://docs.nops.io/en/articles/5955764-getting-started-with-the-nops-developer-api) to learn how you can get the API key.

If this is your first time onboarding accounts in nOps, click **Proceed to Create API Key**:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694174/47e6cc67a9f2da816edf1ffa/F5oLgrPzC7NufZ7S9XnHRj_TMws81TlnmDK-sw4ROeOiASJSwxOqiFSt0zuaro0hiubaLgSp7daTDOznBLDqtCKYp-900iaSprvbCtENEq-F6OoH8vxIRsnlLx0x3RWRgDcjia3t7fxyqLTja3tJQ0tW6llBvN6_tnPyYhYVxmQYzFyasw1OhW1X0Q)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694174/47e6cc67a9f2da816edf1ffa/F5oLgrPzC7NufZ7S9XnHRj_TMws81TlnmDK-sw4ROeOiASJSwxOqiFSt0zuaro0hiubaLgSp7daTDOznBLDqtCKYp-900iaSprvbCtENEq-F6OoH8vxIRsnlLx0x3RWRgDcjia3t7fxyqLTja3tJQ0tW6llBvN6_tnPyYhYVxmQYzFyasw1OhW1X0Q)

On the second page in the Link **Cloud Accounts** section, enter:

*   An API key name
    
*   API Key description
    
*   Signature verification (optional)
    

After you add all the information, click **Create API Key:**

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694176/23160f54c9a1b4f8e8d4ba9f/1NhJJoETCwMSG3W4Fav7YkVEzVZTHb8QCY2m1h8_K6yRawM5qPoEsyxMvCGln4qJASDmWciFWihfAAcMSgqVIfDtj96S_UcgCnU1dP_7i5WZXAE8-x4MfMJknp7JbV4OV5UYP1IHcaFCP2IcSaOPIh1VpEqvMzc9hH1feLbfXi6LwRHikJ9bKJ__gQ)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694176/23160f54c9a1b4f8e8d4ba9f/1NhJJoETCwMSG3W4Fav7YkVEzVZTHb8QCY2m1h8_K6yRawM5qPoEsyxMvCGln4qJASDmWciFWihfAAcMSgqVIfDtj96S_UcgCnU1dP_7i5WZXAE8-x4MfMJknp7JbV4OV5UYP1IHcaFCP2IcSaOPIh1VpEqvMzc9hH1feLbfXi6LwRHikJ9bKJ__gQ)

Once you click **Create API Key** nOps will generate an API key for you. Copy and save the API key for future use, and click **Next**:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694184/a06303c6ec3af1c1eab89759/r9wcFm7-77_mRJuHgUKgsXQO41DC-MfQo_ZZzXsELEHF34HCx6pzWHjEPXfqCipktaDVgtbx-Lp8zt-kBR5vuApALnhkjJWdVbS8P1OX1-2kQYRNklc5h2eQCvukPRel8OWD3pKZ-_ffoMxgeVOwb4vxLGRhH7JLCCo20QIwOzMBugGKP3VvMIs7zg)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694184/a06303c6ec3af1c1eab89759/r9wcFm7-77_mRJuHgUKgsXQO41DC-MfQo_ZZzXsELEHF34HCx6pzWHjEPXfqCipktaDVgtbx-Lp8zt-kBR5vuApALnhkjJWdVbS8P1OX1-2kQYRNklc5h2eQCvukPRel8OWD3pKZ-_ffoMxgeVOwb4vxLGRhH7JLCCo20QIwOzMBugGKP3VvMIs7zg)

When you click next, nOps will start checking for its connectivity with your AWS accounts. In order for nOps to establish a connection with your accounts and start the data ingestion, you need to:

1.  Enable Stackset in AWS Organizations and AWS CloudFormation.
    
2.  Go to AWS CloudFormation and create a Stack for the Master Payer account.
    
3.  Log in to the Master Payer account and create a Stackset for the child/member accounts.
    

Once you complete these two steps, come back to the nOps setup, and you will see the following screen. Click **Refresh**.

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694195/51ef218d885ca96914646dd1/e1F84PFIziBiBRLKT-kRMAyYq-4s768J3O9Hs86KtvcwFIVOjB7vg6NJmFfY11_Tbu1jlXSkHwhIEYgWGm1ceoXnkIigN5nSbn6B8kyyM_CBcJEApmg5CMelmbXpt7U59xrufjS85aZwtQTC-vqSYUgVN38kH7TAp0hRzfB6l-BKY2BXidtuL_bkMA)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694195/51ef218d885ca96914646dd1/e1F84PFIziBiBRLKT-kRMAyYq-4s768J3O9Hs86KtvcwFIVOjB7vg6NJmFfY11_Tbu1jlXSkHwhIEYgWGm1ceoXnkIigN5nSbn6B8kyyM_CBcJEApmg5CMelmbXpt7U59xrufjS85aZwtQTC-vqSYUgVN38kH7TAp0hRzfB6l-BKY2BXidtuL_bkMA)

Enable Stacksets
----------------

To enable _CloudFormation StackSets_ in _AWS Organizations_, go to **AWS Organizations > Services**. If you see **Access disabled** against _CloudFormation StackSets_, enable it.

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694204/26e92598911ebab07fa93531/GKYaHMHoV51kq3vrOOPAuOFuV2U1pRejcbVCzaVhqvnP2ArrHu2J6Y0nt-9KjqoSI-ucaE5IQDDFtb9XRvGxK4siLt1MmLMo4ImkH493-CN3XWI4Gpr2aN1guyj16uzkT7UxsW1uSrk5GJf--UlRARxqe3mI8OdY8ef3Ff0vyG_ZnqTIdpV1wxlgVw)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694204/26e92598911ebab07fa93531/GKYaHMHoV51kq3vrOOPAuOFuV2U1pRejcbVCzaVhqvnP2ArrHu2J6Y0nt-9KjqoSI-ucaE5IQDDFtb9XRvGxK4siLt1MmLMo4ImkH493-CN3XWI4Gpr2aN1guyj16uzkT7UxsW1uSrk5GJf--UlRARxqe3mI8OdY8ef3Ff0vyG_ZnqTIdpV1wxlgVw)

Once enabled, against _CloudFormation StackSets_, you should see **Access enabled**:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694214/0e739db266f1edeb76e4f389/dz7fwbnd_xfy5MMGEjr80oThQtY9r_xhI9Whmm2K0yOQJKKM7OXSXg4yGQ0Mb8zGDiqAWsfCF_t0a1YabvVnTFd18sl0xs-vFSHR8j7heu8rDuhZASkNt3_O1LkKFbRSiXBEdPdCfgv0UxkbWtwSkW8XGS0KGVrhqKFkGheeyi6Q3SEU9bNtp87GJQ)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694214/0e739db266f1edeb76e4f389/dz7fwbnd_xfy5MMGEjr80oThQtY9r_xhI9Whmm2K0yOQJKKM7OXSXg4yGQ0Mb8zGDiqAWsfCF_t0a1YabvVnTFd18sl0xs-vFSHR8j7heu8rDuhZASkNt3_O1LkKFbRSiXBEdPdCfgv0UxkbWtwSkW8XGS0KGVrhqKFkGheeyi6Q3SEU9bNtp87GJQ)

To enable StackSets in _AWS CloudFormation_, go to **CloudFormation > StackSets**. If there is no prompt to enable _StackSets_, then skip this step.

If you see an option to enable the _StackSets_, then enable it:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694222/617eb225958e1b5508350866/lA99H8cN2SpWXta-mY3VTQ8-2vTPNv-Xpm0Evnt7_90VQ43lySXZB-3htkut_diwuDt8WAFhioyEyrhFyB1m08uQasT2KtXXfcDZDChWWHAQyGZRuc7TFwUMNOgTJHjIRq4zxG5Oa0DEFJwPgaAMMVzqjnZERxpHHOOlNUQex2zxqb4r-6LFSzgFrw)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694222/617eb225958e1b5508350866/lA99H8cN2SpWXta-mY3VTQ8-2vTPNv-Xpm0Evnt7_90VQ43lySXZB-3htkut_diwuDt8WAFhioyEyrhFyB1m08uQasT2KtXXfcDZDChWWHAQyGZRuc7TFwUMNOgTJHjIRq4zxG5Oa0DEFJwPgaAMMVzqjnZERxpHHOOlNUQex2zxqb4r-6LFSzgFrw)

Create a Stack for the Master Payer Account
-------------------------------------------

Stack is a regional service for single account deployment, which in this case, is the Master Payer account. First, we will deploy a Cloudformation Stack in the Master Payer Account. Then we will log into the Organization Master Account to create a Stackset for the Child Accounts (OUs).

* * *

**Note:** It is important to note that an Organization Master Account != Master Payer account. A child account can also be a Master Payer account, but a child account can never be an Organization Master Payer Account.

* * *

To create a stack for the Master Payer Account account, go to **AWS Console > CloudFormation > Stacks** page and click **Create stack > With new resources (standard)**.

The creation of a stack is divided into 4 steps:

**In Step 1 (Specify template)** —

1.  In the **Specify template** section, choose **Upload a template file** option.
    
2.  Click **Choose file**:
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694227/03a4be7a84287980951ac894/Zb_2I5FaLp8sDD7mLZiCsme8_YgJqton5IA5H0YVGy1KKLjuJviGqUU47AEXrjuV3X4Fr_2jBTsefQYfE3hon8xsyXSWrJYFETuTfmnEnEM7D0YeTMsovIXj6nECrv8ucQ0DqcegcQSWO6KL9Fh3byQWh4TQ1HBzPO-Zd4EIS73Ys9grwnYyT07IXg)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694227/03a4be7a84287980951ac894/Zb_2I5FaLp8sDD7mLZiCsme8_YgJqton5IA5H0YVGy1KKLjuJviGqUU47AEXrjuV3X4Fr_2jBTsefQYfE3hon8xsyXSWrJYFETuTfmnEnEM7D0YeTMsovIXj6nECrv8ucQ0DqcegcQSWO6KL9Fh3byQWh4TQ1HBzPO-Zd4EIS73Ys9grwnYyT07IXg)
    
3.  When you click **Choose file**, AWS will open a navigation window for you to navigate and select the YAML template in your local machine. In your local copy of the repository navigate to **nops-cloud-account-registration/nops-aws-account-register/cloudformation-single-acc-register/** and select the **nops\_register\_aws\_acc.yaml** file.
    
4.  Click **Next**.
    

**In Step 2 (Specify stack details)** —

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694230/b6c9e8480558bafa5fdf43af/ns4RYGm6ls5LavB1E8JKXQ6IKVoIcTan0Ziwnx1lIQtVKu6sPpHhRDGO8nwtCLtGurdzm6C6kjiXxCe9yFxmPC43o4fqMOsb-nPkf5hyymt72qlCpMhkw6vTDnqAhsnCHHZ6Z5FPcUPDZa38hAbjBqqUmFVf9UIxCTlaljhqDqIkZ53agx8mquVEIA)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694230/b6c9e8480558bafa5fdf43af/ns4RYGm6ls5LavB1E8JKXQ6IKVoIcTan0Ziwnx1lIQtVKu6sPpHhRDGO8nwtCLtGurdzm6C6kjiXxCe9yFxmPC43o4fqMOsb-nPkf5hyymt72qlCpMhkw6vTDnqAhsnCHHZ6Z5FPcUPDZa38hAbjBqqUmFVf9UIxCTlaljhqDqIkZ53agx8mquVEIA)

1.  Provide a **Stack name**.
    
2.  Enter the **account name to register** in nOps.
    
3.  Provide the **nOpsAPIKey**.
    
4.  Enter **nOpsPrivateKey** with a single slash instead of a double slash since we are using CloudFormation directly.
    
5.  Click **Next**.
    

**In Step 3 (Configure stack options)** — leave every field to its default and click **Next**.

**In Step 4 (Review)** —

1.  Review the stack details.
    
2.  Check the **“I acknowledge that AWS CloudFormation might create IAM resources”** checkbox (important).
    
3.  Click **Create stack**
    

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694236/9dc029882f38f327f940fc12/iAnJCl7WCLWctw-teMJ3B4v4JMzOXtQhbHzIfYyA3xwVeS_kOMgFZ5e7Tq33AzQ3h4oepiFxqIEvfv5h8ue7UYtfu38gWjsgInCK95yewZVo8DUeonvV2kVpqsyZqOzh6EqaUUN2t5LMtEV4uyFb1l528nBsO9rScnUwH4DFKMaGgfB1PsKdmdLHEw)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694236/9dc029882f38f327f940fc12/iAnJCl7WCLWctw-teMJ3B4v4JMzOXtQhbHzIfYyA3xwVeS_kOMgFZ5e7Tq33AzQ3h4oepiFxqIEvfv5h8ue7UYtfu38gWjsgInCK95yewZVo8DUeonvV2kVpqsyZqOzh6EqaUUN2t5LMtEV4uyFb1l528nBsO9rScnUwH4DFKMaGgfB1PsKdmdLHEw)

Create a Stackset for the Child/Member Accounts
-----------------------------------------------

Stackset is multi-account and multi-region. To create and deploy a stackset for the Child accounts, make sure that you are logged into your Master Account.

To create a stackset for the Child/Member account, log in to AWS with your Master Payer Account, go to **AWS Console > CloudFormation > Stacksets** page, and click **Create Stackset**. The creation of a Stackset is divided into 5 steps:

**In Step 1 (Choose a template)** —

1.  In the **Specify template** section, choose **Upload a template file** option.
    
2.  Click **Choose file**:
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694240/838e9756ad1b19e351da5c29/u9-uCIl9PotBlabUIb-JRjqfeJtIWpwNhQCB_A2MkXLdQVhg1CyieaedDThpstt0_zl2j-XGurQckUa1LU7CqHUOQaiqw2BetrQIwmX2LERAUBImsjjxaiR7WilxkC9UeGLEyFplSoZ7RC_zvIdfkbEtnJiCbk4VR956ee1FNR4qfXQyIMXi4FNCKA)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694240/838e9756ad1b19e351da5c29/u9-uCIl9PotBlabUIb-JRjqfeJtIWpwNhQCB_A2MkXLdQVhg1CyieaedDThpstt0_zl2j-XGurQckUa1LU7CqHUOQaiqw2BetrQIwmX2LERAUBImsjjxaiR7WilxkC9UeGLEyFplSoZ7RC_zvIdfkbEtnJiCbk4VR956ee1FNR4qfXQyIMXi4FNCKA)
    
3.  When you click **Choose file**, AWS will open a navigation window for you to navigate and select the YAML template in your local machine. In your local copy of the repository navigate to **nops-cloud-account-registration/nops-aws-account-register/cloudformation-org-member-accounts-register/** and select the **_member\_consolidated\_aws\_acc\_nops\_register.yaml_** file.
    
4.  Click **Next**.
    

**In Step 2 (Specify Stackset details)** —

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694242/ac0c03a516c3588630c82b0e/Rgfa-RHn7rOkgROY1IaowV-3krZtfVlizutiKam27BSiSWf3ntRJcmEoqvgJpDrElDb9tA0BJQTAYX4H_fyABYeuqem6unGSLvzn6ZHrNbH7NgeqJexTJFaaqr_Fm3VCjAyIqtV03syHawgh3G9juQFpHFF1RtybTCbUD1AIDUimJMSF1rac367ieA)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694242/ac0c03a516c3588630c82b0e/Rgfa-RHn7rOkgROY1IaowV-3krZtfVlizutiKam27BSiSWf3ntRJcmEoqvgJpDrElDb9tA0BJQTAYX4H_fyABYeuqem6unGSLvzn6ZHrNbH7NgeqJexTJFaaqr_Fm3VCjAyIqtV03syHawgh3G9juQFpHFF1RtybTCbUD1AIDUimJMSF1rac367ieA)

1.  Provide a **StackSet name**.
    
2.  Enter the **account name to register** in nOps.
    
3.  Provide the **nOpsAPIKey**.
    
4.  Enter **nOpsPrivateKey** with a single slash instead of a double slash since we are using CloudFormation directly.
    
5.  Click **Next**.
    

**In Step 3 (Configure Stackset options)** —

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694246/c13802903cf72a6ce37f7a45/bfcAIxZAadIVciFoeM8GcMwhlkDR3ILWBHKsK0JKSNNqTzcTlIICplKQgSAwTRjpOTGo5bIPycT1fNNVCJtRNeGwIcysRprLk2pxDUR0IvtsHBE7PEAZ_n64NbNnxBfCVXP3-2CnCLbH4PX0nDoiixDfLkyOvI95SVITrCURJ_ggWLN6Opdd8mmouA)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694246/c13802903cf72a6ce37f7a45/bfcAIxZAadIVciFoeM8GcMwhlkDR3ILWBHKsK0JKSNNqTzcTlIICplKQgSAwTRjpOTGo5bIPycT1fNNVCJtRNeGwIcysRprLk2pxDUR0IvtsHBE7PEAZ_n64NbNnxBfCVXP3-2CnCLbH4PX0nDoiixDfLkyOvI95SVITrCURJ_ggWLN6Opdd8mmouA)

1.  In the **Execution configuration** section, select the **Inactive** option.
    
2.  Click **Next**.
    

**In Step 4 (Set deployment options)** —

1.  In the **Add stacks to stack set** section, select the **Deploy new stacks** option.
    
2.  In the **Deploy targets** section, select the **Deploy stacks in organizational units** option.
    
3.  Provide the organizational unit ID.
    
4.  In the **Specify regions sectio**n, select your desired region.
    
5.  In the **Deployment options** section, select the **Parallel** option (optional).
    
6.  Click **Next**
    

**In Step 5 (Review)**, review and create the stackset.

Fetching
--------

Once the stacksets are created and your AWS accounts are linked successfully, you will see the following screen:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694252/987986e5f8c1c3033d04e659/a5nhxPpnLTE-rEBxAOFi9bpdPQorEkA23Lt65yqBzAVe1jJ_yQ1FgnTs40oqHMzc3c144hd0zoDa5pISjM01Hyfk8q_mnbiftomz5h8uJ27mHnS4thx0hUC2DBP0DStjtcAoe9nbqmq-8XA28FJ8VvbiEcBrkQoNNuJMNqlASfh1gUf7EmlwVytQog)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/585694252/987986e5f8c1c3033d04e659/a5nhxPpnLTE-rEBxAOFi9bpdPQorEkA23Lt65yqBzAVe1jJ_yQ1FgnTs40oqHMzc3c144hd0zoDa5pISjM01Hyfk8q_mnbiftomz5h8uJ27mHnS4thx0hUC2DBP0DStjtcAoe9nbqmq-8XA28FJ8VvbiEcBrkQoNNuJMNqlASfh1gUf7EmlwVytQog)

It might take several hours for nOps to fetch the data from your AWS account.

After the data is fetched, the setup process is now complete.

Note: It can take up to 24 hours before you start seeing the different nOps dashboards and compliance views populated with data from your workload.

If you have any questions, please contact us at [help@nops.io](mailto:help@nops.io), or by phone at +1 866-673-9330.

On initial ingestion, nOps will pull the data from AWS accounts based on the following durations:

*   Cost data: 6 months look back + current month.
    
*   Rules: Current date.
    
*   CloudTrail Events: 14 days look back.