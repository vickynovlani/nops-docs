---
title: Backfilling a CUR file for MAP
parent: MAP
grand_parent: User Guides
nav_order: 3
layout: default
---

{: .no_toc }

# Backfilling a CUR file for the MAP program #

If you're participating in AWS's Migration Assistance Program, you want to get the maximum credit from the MAP program.

One thing to consider is a longer trail of data within your Cost and Usage Report (CUR).  In order to get the most out of nOps, we recommend filling out a support ticket with AWS to do a CUR backfill.  This will load your CUR file with previous months' data, allowing you to get better insight.


- TOC
{:toc}

## Creating the Ticket ##

For each Payer account, log into your [Amazon Support Console](https://support.console.aws.amazon.com/support) to create a support ticket

### Ticket Information ###

**Type**: Billing
**Category**: Invoices and Reports
**Subject**: Backfill CUR reports
**Description**:

Please Backfill The CUR for the following:
**CUR Report name**: nopsbilling-hourly-parquet
**Time Period**: <Enter the MAP Start Month> to <Enter the Month prior to the data in nOps>
**Reason**: We moved to a finance reporting engine for tracking MAP credits that requires all CURs to be in parquet format
