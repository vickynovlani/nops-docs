---
title: YAML file for CUR, S3 bucket, IAM Policy, and nOps ShareSave linked accounts to your AWS Organization
parent: Getting Started with nOps
nav_order: 9
layout: default
---

**YAML file for CUR, S3 bucket, IAM Policy and nOps ShareSave linked accounts to your AWS Organization**

## Prerequisites ##
=================

To take advantage of all nOps ShareSave Program, **you must subscribe ONCE to nOps AWS Marketplace offering.** If you have previously subscribe, you are all set to take advantage of all of nOps ShareSave Programs. If not, it’s easy to subscribe and nOps will not charge anything unless we save you money:

1.  Log in to your AWS Payer/Management account with your IAM user.
2.  Click the for Following link: [nOps AWS Marketplace Offering](https://aws.amazon.com/marketplace/pp/prodview-xcwcwhkhkjxdw?sr=0-2&ref_=beagle&applicationId=AWS-Marketplace-Console)
3.  Once on the nOps offering, Click “**View Offering**“, “**Subscribe**” and finally “**setup Account**“.. That’s it, your done, now time to save!  
    

## Steps for **Automated** Setup for Auto-Pilot Risk-Free Commitment Management ##
====================================================================================

The automated setup is simple, easy and takes only 5 minutes:

1.  On your **AWS Payer/Management account,** nOps will create a new hourly Cost/Usage Report(CUR), S3 bucket for the CUR and nOps ShareSave Payer cross-account role/policy :  
    1.  _Trusted Entity Type_: AWS Account
    2.  _Trusted Entity_: nOps
    3.  _Role name_: nops-sharesave-payer
    4.  _IAM Policy for the Role_: [IAM Policy](https://help.nops.io/en/aws-setup-permissions-sharesave-auto-pilot-risk-free-commitment-management#h_e5732f6dbf)
    5.  _Automated Creation_: [YAML File](https://help.nops.io/en/aws-setup-permissions-sharesave-auto-pilot-risk-free-commitment-management#h_06c2073ab6)
2.  nOps will link **two nOps ShareSave accounts** to your AWS Organization in your AWS Payer/Management account:  
    
    1.  **ShareSave Compute &lt;xx&gt;** – used by nOps to buy/sell EC2 3-year Standard Reserved Instances and buy 3-year Compute Savings Plans.  
        1.  _Trusted Entity Type_: AWS Account_Trusted Entity_: nOps_Role name_: nops-sharesave-ri_IAM Policy for the Role_: [IAM Policy](https://help.nops.io/en/aws-setup-permissions-sharesave-auto-pilot-risk-free-commitment-management#h_dbee600031)_Automated Creation_: NA – preloaded  
            
    
    1.  **ShareSave Other &lt;xx&gt;** – used by nOps to buy current generation/flexible 1-year Reserved Instances for RDS, Redshift, OpenSearch, and ElasticCache.  
        1.  _Trusted Entity Type_: AWS Account
        2.  _Trusted Entity_: nOps
        3.  _Role name_: nops-sharesave-ri
        4.  _IAM Policy for the Role_: [IAM Policy](https://help.nops.io/en/aws-setup-permissions-sharesave-auto-pilot-risk-free-commitment-management#h_dbee600031)
        5.  _Automated Creation_: NA – preloaded

**How to kick off the automated setup and to begin Saving!**
============================================================

To begin savings via **nOps ShareSave – Auto-Pilot Risk-free Commitment Management**, follow these steps:

1.  Log in to your **AWS Payer/Management account** with your IAM user
2.  In another tab, Log in to your **nOps Client** and head over to the **ShareSave** dashboard:[](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/604505191/bef5b26ae129b4b4ee1b16c5/Gz1kVRMX81Gq9jZARvr_A7IVvAhnHjrGlhBUwDtYJj97kMQaMVexsNDmLMPyWt_iJnAIefIUje4D9bWG3roZ3vG89b_Ja-pccTLMY4upc_i3JtKQisKqkD6c7rdD7MpGrbRjHra3AQ1K9yrFjzThtlrTPC9AJH1EZxGztTsXlDrR4kgCcyvd5pyl1A)
3.  On the **ShareSave Opportunity** dashboard, in the **List of Opportunities** section, click the **Configure Risk Free Commitment** button:[](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/604505197/b155de782fe4ea104e0cd514/kOEYheqbyuS9UVbmc7xOCHsoKC7F78HLtO06BOrUXBHhyK5MaNmLuojFpGJKdBaItxCfGgxDiCSKNP4WGIW8WGnH499GAQjrK2dyBiWqmlvBipVmAzYLwTiNf_jALJnV2t_-z4iTmNMknZ2nK33RR0IMz1YAMOQ6WOzwMlkLjZEpj014pKTUWBTjQA)
4.  Once you click the **Configure Risk Free Commitment** button, the following pop-up will appear:[](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/604505204/347a768573137a2fabfd2a7b/Cp70MH_w1hqcLMNNjqIV-rg90waWT3HanHYzS5wKgWxwUSapfitd21vQBTqbFhf54uCNBCg8XYINhH9lYmh4d2f7aDTmRV0RwxfQLD9Z-1X4zwa-_fLoIML7FYC2TU2VHtb-xhGQ2E35d_kgukNQWoOdPWfjFfZfLAjkYqzOsJo-5F16Yt17g6X4FQ)
    1.  If the pop-up does not appear, make sure that the pop-up isn’t being blocked by your browser.
    2.  **Before you click Proceed, make sure that you’re logged in to your AWS Payer/Management account in the same browser.**
5.  After you click **Proceed**, nOps will take you to your AWS console’s CloudFormation **Quick create stack** page —with all the required information pre-filled  
    **Acknowledge** and click **Create stack**:[](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/604505212/e5773e66a100d8a3c1b9cc13/0HQy_xxqekhqZ2G0RqwCcvJSJRc9rzeuI86wfgKSex4MuDg22xxe6FQLRmct8IPwbAFB93EyZLb3fm-VGip1u3qVZZsh7OdgNW-woumxlzauRd1tEAPCvsfQxVzVprc_RRGyVgj8h1i0tBcGM95jY0RFWjJFY51HRfWLRmkiWUUWk4R0unil_cmzEg)  
    NOTE: The CloudFormation will take about 3-5mins to complete
6.  Once the CloudFormation has completed, go to **AWS Organizations via the AWS Console** to see the two nOps ShareSave Accounts added

![](https://help.nops.io/wp-content/uploads/2023/03/sharesave-aws-organization--1024x924.png)

ShareSave: Auto-Pilot Risk-Free Commitment Management configuration is now complete.

* * *

**_Note: It will take up to 7 days for nOps Auto-Pilot Risk-Free Commitment Management AI to begin buying commitments within the ShareSave accounts_**

**Referenced Information from Above:**
======================================

**AWS Payer/Management Account, YAML File for CUR, S3 bucket, and nOps Role/Policy**
====================================================================================

```yaml
AWSTemplateFormatVersion: "2010-09-09"

Description: |
  nOps.io integration role for ShareSave accounts (updated September 12, 2022)
  For more information visit http://help.nops.io

Parameters:
  S3CurBucket:
    Description: Format  customername-sharesave
    Type: String
  ReportName:
    Description:  Format  customername-sharesave
    Type: String

Resources:
  CURBucketCreate:
    Type: "AWS::S3::Bucket"
    DeletionPolicy: Retain
    Properties:
      BucketName: !Ref "S3CurBucket"

  CURBucketPolicy:
    Type: "AWS::S3::BucketPolicy"
    DeletionPolicy: Retain
    DependsOn: CURBucketCreate
    Properties:
      Bucket: !Ref "S3CurBucket"
      PolicyDocument:
        Statement:
          - Action:
            - "s3:GetBucketAcl"
            - "s3:GetBucketPolicy"
            Effect: Allow
            Resource: !Join ["", ["arn:",!Ref AWS::Partition,":s3:::",!Ref "S3CurBucket"]]
            Principal:
              Service:
              - billingreports.amazonaws.com
          - Action:
            - "s3:PutObject"
            Effect: Allow
            Resource: !Join ["", ["arn:",!Ref AWS::Partition,":s3:::",!Ref "S3CurBucket","/*"]]
            Principal:
              Service:
              - billingreports.amazonaws.com

  CURCreate:
    Type: "AWS::CUR::ReportDefinition"
    DeletionPolicy: Retain
    DependsOn: CURBucketPolicy
    Properties:
      ReportName: !Ref "ReportName"
      RefreshClosedReports: True
      S3Bucket: !Ref "S3CurBucket"
      S3Prefix: sharesave
      S3Region: us-east-1
      TimeUnit: HOURLY
      ReportVersioning: OVERWRITE_REPORT
      AdditionalArtifacts:
        - REDSHIFT
      Compression: GZIP
      Format: textORcsv

  nOpsShareSaveRole:
    Type: "AWS::IAM::Role"
    DependsOn: CURBucketPolicy
    Properties:
      RoleName: nops-sharesave-payer
      AssumeRolePolicyDocument:
        Version: 2012-10-17
        Statement:
          - Effect: Allow
            Principal:
              AWS:
                - arn:aws:iam::727378841472:root
            Action:
              - "sts:AssumeRole"
      Path: /
      Policies:
        - PolicyName: nops-sharesave-policy
          PolicyDocument:
            Version: 2012-10-17
            Statement:
              - Sid: S3ViewCUR
                Effect: Allow
                Action:
                  - "s3:ListBucket"
                Resource: !Join ["", ["arn:",!Ref AWS::Partition,":s3:::",!Ref "S3CurBucket"]]
              - Sid: S3AccessCUR
                Effect: Allow
                Action:
                  - "s3:GetObject"
                  - "s3:PutObject"
                  - "s3:DeleteObject"
                Resource: !Join ["", ["arn:",!Ref AWS::Partition,":s3:::",!Ref "S3CurBucket","/*"]]
      ManagedPolicyArns:
        - "arn:aws:iam::aws:policy/AWSSupportAccess"

```

**AWS Payer/Management Account: IAM Policy**
============================================

```json

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "s3:ListBucket"
            ],
            "Resource": "arn:aws:s3:::<YOUR BUCKET NAME HERE>",
            "Effect": "Allow",
            "Sid": "S3ViewCUR"
        },
        {
            "Action": [
                "s3:GetObject",
                "s3:PutObject",
                "s3:DeleteObject"
            ],
            "Resource": "arn:aws:s3:::<YOUR BUCKET NAME HERE>/*",
            "Effect": "Allow",
            "Sid": "S3AccessCUR"
        }
    ]
}

```
**nOps ShareSave Accounts: IAM Policy nOps uses to Buy/Sell Reservations and Savings Plans**
============================================================================================

```json

{
    "Version": "2012-10-17",
    "Statement": [
            {
        "Action": [
            "ec2:DescribeReservedInstances",
            "ec2:DescribeReservedInstancesListings",
            "ec2:DescribeReservedInstancesModifications",
            "ec2:DescribeReservedInstancesOfferings",
            "ec2:ModifyReservedInstances",
            "ec2:PurchaseReservedInstancesOffering",
            "ec2:CreateReservedInstancesListing",
            "ec2:CancelReservedInstancesListing",
            "ec2:GetReservedInstancesExchangeQuote",
            "ec2:AcceptReservedInstancesExchangeQuote",
            "rds:DescribeReservedDBInstances",
            "rds:DescribeReservedDBInstancesOfferings",
            "rds:PurchaseReservedDBInstancesOffering",
            "support:*",
            "SavingsPlans:*"
            ],
            "Effect": "Allow",
            "Resource": "*"
        }
    ]
}

```