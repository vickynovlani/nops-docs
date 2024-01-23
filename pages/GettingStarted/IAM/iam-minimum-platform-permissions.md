---
title: Minimum IAM permissions for the nOps platform
keywords: iam policies, iam, setup, onboarding, permissions
tags: [onboarding, iam]
sidebar: mydoc_sidebar
permalink: iam-minimum-platform-permissions.html
folder: GettingStarted
series: [Onboarding, IAM]
weight: 1.0
---

## IAM Policy Minimum Permissions for the nOps Platform in YAML ##

The following yaml file shows the minimum permissions necessary for the nOps free platform.

```yaml
NopsIntegrationPolicy:
    Type: AWS::IAM::Policy
    Properties:
      PolicyName: NopsIntegrationPolicy
      PolicyDocument:
        Version: "2012-10-17"
        Statement:
          - Action:
              - ce:GetSavingsPlansUtilizationDetails
              - ce:GetSavingsPlansUtilization
              - ce:GetSavingsPlansPurchaseRecommendation
              - ce:GetSavingsPlansCoverage
              - ce:GetReservationUtilization
              - ce:GetReservationPurchaseRecommendation
              - ce:GetReservationCoverage
              - ce:GetCostAndUsage
            Effect: Allow
            Resource: "*"
      Roles: [!Ref NopsIntegrationRole]

  NopsSystemBucketPolicy:
    Type: AWS::IAM::Policy
    Properties:
      PolicyName: NopsSystemBucketPolicy
      PolicyDocument:
        Version: "2012-10-17"
        Statement:
          - Effect: Allow
            Action:
              - s3:*
            Resource:
              - !Sub "arn:aws:s3:::${SystemBucketID}"
              - !Sub "arn:aws:s3:::${SystemBucketID}/*"
              - !Sub "arn:aws:s3:::${SystemBucketID}-nops-${AWS::AccountId}"
              - !Sub "arn:aws:s3:::${SystemBucketID}-nops-${AWS::AccountId}/*"
      Roles: [!Ref NopsIntegrationRole]
```

{% include custom/series_related.html %}