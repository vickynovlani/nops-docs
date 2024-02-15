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

## IAM Policy Minimum Permissions for the nOps Platform in JSON ##

The following json file shows the minimum permissions necessary for the nOps free platform.

```json

{
	"Version": "2012-10-17",
	"Statement": [
	    {
			"Sid": "VisualEditor1",
			"Effect": "Allow",
			"Action": "s3:*",
			"Resource": [
				"arn:aws:s3:::[INSERT CUR S3 BUCKET]",
				"arn:aws:s3:::[INSERT CUR S3 BUCKET]/*"
			]
		},
		{
			"Sid": "VisualEditor0",
			"Effect": "Allow",
			"Action": [
				"organizations:InviteAccountToOrganization",
				"tag:GetResources",
				"ec2:DescribeInstances",
				"rds:DescribeDbClusters",
				"s3:ListBucket",
				"cloudwatch:GetMetricStatistics",
				"cur:PutReportDefinition",
				"rds:DescribeDbInstances",
				"cur:DeleteReportDefinition",
				"ec2:DescribeSecurityGroups",
				"eks:DescribeNodegroup",
				"ec2:DescribeNetworkInterfaces",
				"autoscaling:DescribeAutoScalingGroups",
				"ec2:DescribeVpcs",
				"ec2:DescribeVolumes",
				"eks:DescribeCluster",
				"ec2:DescribeReservedInstances",
				"eks:ListClusters",
				"ce:*",
				"ec2:DescribeSubnets",
				"cur:DescribeReportDefinitions"
			],
			"Resource": "*"
		}
	]
}

```

{% include custom/series_related.html %}