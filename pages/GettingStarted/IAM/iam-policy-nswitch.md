---
title: IAM permissions for nOps nSwitch
keywords: iam policies, iam, setup, onboarding, nswitch, sharesave
tags: [getting_started, onboarding, iam, sharesave, nswitch]
sidebar: mydoc_sidebar
permalink: iam-policy-nswitch.html
folder: GettingStarted
---


# ShareSave nSwitch resource scheduler IAM permissions #


As a part of the [free nOps platform](iam-policy-nops-free-platform.html), we analyze your Cost and Usage Report (CUR). As a part of the free nOps platform, we analyze your Cost and Usage Report (CUR) and provide you with scheduler recommendations that you can automate.

In order to extract the full potential of the nOps Scheduler, you need permissions for two nOps features:

* **[ShareSave nSwitch Resource Scheduler](iam-policy-nswitch.html)**: To get the scheduling recommendations.
* **[nSwitch using Eventbridge](#scheduler-permissions-lambda-and-eventbridge)**: To automate the scheduling of resources based on the ShareSave Resource Scheduler recommendations.

_Note: To enable nSwitch recommendations for any child account, it is necessary to get the account fully configured. I.e to enable the [ReadOnly policy](iam-policy-nops-free-platform.html#linked-account-iam-policy-json) access at the child account level._

## Access CUR data to analyze utilization ##

The permissions required at the payer and linked account(s) for ShareSave nSwitch are:

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


nOps requires AWS managed [AWSLambdaBasicExecutionRole](https://console.aws.amazon.com/iam/home#policies/arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole) permissions along with the following permission for Scheduler Lambda Function to automatically create schedules with the help of [EventBridge](using-nswitch-to-reduce-costs.html):

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