---
title: Check Multi-Factor Authentication
keywords: reporting, security
tags: [reporting, compliance]
sidebar: mydoc_sidebar
permalink: security-mfa-activated.html
folder: UserGuides
---

# Check if the Root Account has MFA Activated



## How to Check if the Root Account MFA status ##
===========================================

nOps has the option of checking security across your AWS account that it is connected with. One crucial part of the AWS account is the root account. The maximum-security has to be applied to it, else any vulnerability or risk found and exploited can be devastating to the whole AWS account. Let us show you how to check if MFA is activated for your AWS account

Click on the **Security Dashboard** menu item, which is one of the top menu items.

This will lead to the **_Security Compliance_ Dashboard**. This dashboard displays different rules and violations. On the page **_IAM Role Permission_** **and** **Account Usage**. Scroll to the item called **AWS accounts doesn’t have root account MFA.**


This shows if the root user has MFA enabled or not. Clicking on the arrow on this row, will display who is not in compliance

![](/tmpimg/mfa-action-arrow.png)

![](/tmpimg/root-wo-mfa.png)