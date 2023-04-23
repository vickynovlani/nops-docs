---
title: PagerDuty Integration
keywords: reporting, integrations
tags: [agents_integrations]
sidebar: mydoc_sidebar
permalink: pagerduty-integration.html
folder: Integrations_and_Agents
---

Integrating PagerDuty into your cloud optimization workflow for better alerting.

1. TOC
{:toc}

PagerDuty Integration with nOps
===============================

You can use your PagerDuty service to receive the security audit trail related to security best practices from nOps. These security best practices are implemented using different nOps rules. Whenever there is a change in violations, a security audit trail is generated. Follow the steps below to integrate PagerDuty with nOps now.

Steps to Integrate PagerDuty.
-----------------------------

Create a new service in PagerDuty

Go to **Configuration → Services → New Service**

![](/tmpimg/create-pd-service.png)

From the new created service, **click on New Integration**

![](/tmpimg/pd-add-int.png)

This new integration will help in generating a new API key that can be added to the set security audit trail

![](/tmpimg/pd-created.png)

Login to nOps and go to logged-in name to show the **Settings** icon. On the Settings Page, click on **Integrations**. In the Integrations page, click PagerDuty Integration. Enter the PagerDuty Integration Key.

![](/tmpimg/pd-int-enter-key.png)