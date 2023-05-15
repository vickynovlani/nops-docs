---
title: Generate an AWS Cost and Usage Report
keywords: setup, onboarding, CUR
tags: [getting_started, onboarding]
sidebar: mydoc_sidebar
permalink: onboarding-generate-a-cur.html
folder: GettingStarted
---


# How to Generate an AWS Cost and Usage Report (CUR) #


AWS provides a convenient way to view and track your usage and costs through the AWS Management Console. However, to analyze your usage and costs more effectively, you may need more detailed information. That's where the AWS Cost and Usage Report (CUR) comes in. The CUR provides detailed usage and cost data for your AWS resources, and you can use it to create custom reports or perform cost and usage analyses. In this article, we will discuss how to request AWS to generate a CUR and how far back it usually goes.


## Requesting AWS to Generate a CUR ##


To generate a CUR, you need to request it through the AWS Management Console. Follow these steps:
1. Log in to your AWS account and go to the AWS Management Console.
1. In the Services menu, click on "Cost and Usage Reports" under the "Billing and Cost Management" section.
1. Click on the "Create report" button.
1. In the "Report name" field, enter a name for your report.
1. Select "Hourly" or "Daily" for the "Time unit" field.
1. In the "S3 bucket" field, enter the name of the S3 bucket where you want to store the CUR.
1. (Optional) Select "GZIP" for the "Compression type" field if you want to compress your report.
1. Click on the "Next" button.
1. In the "Report content" section, select the data you want to include in your report.
1. In the "Time range" section, select the time range for your report.
1. In the "Additional report details" section, you can add tags or choose an IAM role for the report.
1. Click on the "Review and complete" button.
1. Review your report settings and click on the "Create report" button.


AWS will start generating your CUR, and you will receive an email notification once it's ready. You can download the report from the S3 bucket you specified during the report creation process.


## How Far Back Does AWS Go with the CUR? ##
AWS keeps a rolling 13 months of cost and usage data. Therefore, if you request a CUR today, you can access cost and usage data going back up to 13 months from the current date. However, keep in mind that the first report you generate may only include data from the day you created the report onwards, as AWS does not store usage and cost data indefinitely.

In conclusion, generating a CUR in AWS is a straightforward process that provides you with detailed cost and usage data for your AWS resources. By requesting a CUR, you can analyze your usage and costs more effectively, create custom reports, and perform cost and usage analyses. Keep in mind that AWS stores 13 months of cost and usage data, and the first report you generate may only include data from the day you created the report onwards.

Depending on th circumstance, you may be able to [Backfill a CUR file](backfilling-a-cur-file.html)