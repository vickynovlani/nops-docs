---
title: AWS Lamda Forwarder Agent
parent: Agents
grand_parent: Integrations and Agents
nav_order: 4
layout: default
---

In this document you will learn how to install the nOps AWS Lambda Forwarder Agent to forward events from your AWS CloudTrail into nOps via CloudFormation stack or Manual Setup.

1. TOC
{:toc}


Requirements
============

Some of the requirements for installing the Lambda Forwarder Agent are:

* [AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-a-trail-using-the-console-first-time.html) with an S3 bucket for CloudTrail logs must be configured before deploying this stack.
    
* The S3 bucket for AWS CloudTrail, and _nops-aws-forwarder_ should be within the same region.
    
* API key from nOps. If you want to use an encrypted key, set up a symmetric encryption key within KMS in the same region of Lambda and provide the permission for Lambda execution's role later.
    

Installation
============

The recommended way to install the Lambda Forwarder Agent is to use the CloudFormation stack, but if for some reason the installation fails or you don’t want to use CloudFormation, you can also install the agent manually.

CloudFormation
--------------

In order to start the installation process, log into your admin AWS account/role and click [deploy the nOps AWS Lambda Forwarder CloudFormation stack](https://console.aws.amazon.com/cloudformation/home#/stacks/create/review?stackName=nops-aws-forwarder&templateURL=https://nops-cloudformation-template.s3.us-west-2.amazonaws.com/lambda-forwarder-cloudformation-template.yaml) to start the deployment of the Forwarder Agent.

* * *

**Note:** To take a look at the CloudFormation template, see [nOps AWS Lambda Forwarder CloudFormation YAML Template](https://nops-cloudformation-template.s3.us-west-2.amazonaws.com/lambda-forwarder-cloudformation-template.yaml).

* * *

When you click the deployment link, you will be redirected to **AWS > CloudFormation > Stacks > Create stack**.

In the **Create stack** page:

1.  Fill in **_pnOpsApiKey_** or **_pnOpsKmsAPIKey_**, **_pCTForwarderReleaseVersion_**, and **_pCloudtrailBucketName_**. All other parameters are optional.
    
2.  Click Create stack, and wait for the creation to complete:
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/575699678/0bc2276c280f264cd01547d1/B3Qxh0kZOyU7np8h_3qmu90OfXXGuUPzBj-8KMCrh6VKA9T5qzIX49Fic6YEnzoi_5_d4o-_nXdVL5WzdNCGiSFMJ8mHkl7NFBlVV6Avjg1Dv0lOacEbpvTfWC0ZNEq8TpLV1D-Mp6cEsNN6XcehICjL0tSoa7Oc49WRekki0waDEs_Rf16tAawF1Q)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/575699678/0bc2276c280f264cd01547d1/B3Qxh0kZOyU7np8h_3qmu90OfXXGuUPzBj-8KMCrh6VKA9T5qzIX49Fic6YEnzoi_5_d4o-_nXdVL5WzdNCGiSFMJ8mHkl7NFBlVV6Avjg1Dv0lOacEbpvTfWC0ZNEq8TpLV1D-Mp6cEsNN6XcehICjL0tSoa7Oc49WRekki0waDEs_Rf16tAawF1Q)
    
3.  You can find the installed forwarder Lambda function under the stack's "Resources" tab with logical ID **rLambdaForwarder**:
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/575699686/432539f8e0737bd4c7c489c3/iHY-O6x5bHTkvjrUhrPJOfQs8LwgI9ZPhRhi9uo78Pc_ZUXe8QLNvWp-ldhfqcgjeC8xBNHUxoUneyQstH4GjdTvH2BV5IOy8oX7O1eRR_WBRonif522kh2xOeY99ur7W72oC0HuyP79uZ6RmTP3y3ujN4SXf-sZyrnLBHc-W9xzjRv04d5DenI1CA)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/575699686/432539f8e0737bd4c7c489c3/iHY-O6x5bHTkvjrUhrPJOfQs8LwgI9ZPhRhi9uo78Pc_ZUXe8QLNvWp-ldhfqcgjeC8xBNHUxoUneyQstH4GjdTvH2BV5IOy8oX7O1eRR_WBRonif522kh2xOeY99ur7W72oC0HuyP79uZ6RmTP3y3ujN4SXf-sZyrnLBHc-W9xzjRv04d5DenI1CA)
    
4.  If you use a KMS-encrypted API key, provide the access permission for the Lambda role for KMS Key
    

Repeat steps 1 to 4 in another region if you operate in multiple AWS regions with a single-region trail.

Manual
------

If you can't install the Forwarder Agent using the provided CloudFormation template or you don’t want to use CloudFormation, you can install the Forwarder Agent manually:

1.  Create a Python 3.9 Lambda function using **nops-aws-forwarder-deployment-package-&lt;VERSION&gt;.zip** from the latest [releases](https://github.com/nops-io/nops-aws-forwarder/releases).
    
2.  Save your [nOps API key](https://app.nops.io/v3/settings?tab=API%20Key) to Lambda's environment variable **NOPS\_API\_KEY** or encrypted KMS key as **NOPS\_KMS\_API_KEY**.
    
3.  Add the **s3:GetObject** permission to the Lambda execution role.
    
4.  Configure [triggers](https://docs.aws.amazon.com/lambda/latest/dg/with-cloudtrail-example.html).
    
5.  If you use a KMS-encrypted API key, provide access permission for the Lambda role for the KMS key.
    

Development
-----------

To update to a new version, run the following:

./deploy\_scripts/bump\_version.sh minor/major/main