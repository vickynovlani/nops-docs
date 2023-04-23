---
title: View IAM Violations
keywords: reporting
tags: [reporting]
sidebar: mydoc_sidebar
permalink: rules-view-iam-violations.html
folder: UserGuides
---

# View IAM Violations


### View IAM security principles that show any violations ###


## How to view IAM violations ##
==========================

IAM violations show you IAM security principles that your account does not comply with. For this to be possible, you must first set up your AWS account(s) on nOps. These violations could range from accounts not using MFA, accounts not granted least privilege To view IAM role violations take the following steps

Go to the **nOps Rules** tab.

![](/tmpimg/nops-rules.png)

**nOps Rules** page will be launched with various tabs showing the different options. Such as **Security, Cost, Reliability, Operations, Performance, and Change Management**

On the left side-bar, there is a section called **Filters**. Under Filters, there is a search bar. In that search bar type the word **IAM**. and press the enter key to search

![](/tmpimg/rules4.png)

This will show a list of IAM violations on the right-hand side. From the screenshot we can see at least 4 sections of violations; 266 AWS IAM roles aren't attached to any resource, 36 users have not been granted least privilege permissions in AWS IAM, 11 active root account access key(s) detected, 6 AWS IAM users aren't using MFA-enabled sign in