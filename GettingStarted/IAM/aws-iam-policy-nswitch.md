---
title: ShareSave nSwitch IAM permissions
parent: IAM Policies
grand_parent: Getting Started
nav_order: 3
layout: default
---

In this article: 

1. TOC
{:toc}
# ShareSave nSwitch resource scheduler IAM permissions #


As a part of the [free nOps platform](../aws-iam-policy-nops-free-platform), we analyze your Cost and Usage Report (CUR). As a part of the free nOps platform, we analyze your Cost and Usage Report (CUR) and provide you with scheduler recommendations that you can automate.

In order to extract the full potential of the nOps Scheduler, you need permissions for two nOps features:

* **[ShareSave nSwitch Resource Scheduler](../aws-iam-policy-nswitch)**: To get the scheduling recommendations.
* **[nSwitch using Eventbridge](#scheduler-permissions-lambda-and-eventbridge)**: To automate the scheduling of resources based on the ShareSave Resource Scheduler recommendations.

_Note: To enable nSwitch recommendations for any child account, it is necessary to get the account fully configured. I.e to enable the [ReadOnly policy](../aws-iam-policy-nops-free-platform.md) access at the child account level._

## Access CUR data to analyze utilization ##
======================================

The permissions required at the payer and Child account for ShareSave nSwitch Scheduler Analysis are:

```json

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": [
        "ce:GetCostAndUsage",
      ],
      "Effect": "Allow",
      "Resource": "*"
    }
  ]
}

```

nOps also required two CUR reports to be configured, with the following bucket access policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": "s3:*",
      "Effect": "Allow",
      "Resource": [
        "arn:aws:s3:::<paste-bucket-name-here>",
        "arn:aws:s3:::<paste-bucket-name-here>/*"
      ]
    }
  ]
}

```

## Scheduler Permissions: Lambda and Eventbridge ##
=============================================

nOps requires AWS managed [AWSLambdaBasicExecutionRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole) permissions along with the following permission for Scheduler Lambda Function to automatically create schedules with the help of [EventBridge](https://help.nops.io/en/utilize-nops-resource-scheduler-with-eventbridge-integration-to-reduce-costs-automatically/):

These permissions are required on the **_child account or master account where the resources to be scheduled reside_**.

```json
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Action": [
            "events:PutEvents",
            "s3:GetObject",
            "s3:PutObject",
            "s3:DeleteObject",
            "s3:GetObjectTagging",
            "ec2:StartInstances",
            "ec2:StopInstances",
            "rds:StopDBInstance",
            "rds:StartDBInstance",
            "logs:PutLogEvents",
            "logs:CreateLogGroup",
            "logs:CreateLogStream",
            "autoscaling:UpdateAutoScalingGroup"
        ],
        "Resource": [
            "*"
        ]
    }]
}

```

To get the full CloudFormation YAML template, see [nOps nSwitch Lambda Function](https://github.com/nops-io/nops-rules-lambda/blob/master/scheduler/scheduler.yml).