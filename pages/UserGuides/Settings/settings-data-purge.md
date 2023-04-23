---
title: Data Purge
keywords: getting started, settings
tags: [getting_started, settings]
sidebar: mydoc_sidebar
permalink: settings-data-purge.html
folder: UserGuides
---


1. TOC
{:toc}

**How nOps purges data**
========================

The data purge policy describes how we purge data after you delete an account and how we remove data.

**Delete account from nOps**
============================

* A client admin will be able to delete AWS account on nOps settings page.
    
* When the admin clicks on delete account in nOps, the account will be scheduled for deletion within 30 days.
    

![](/tmpimg/account-delete.png)

**When the account deletion queue task is executed:**
-----------------------------------------------------

* Deletes all data fetched from AWS API.
    
* Deletes all cost data ingested to nOps.
    
* Keeps user login (email address and password which is used to login to nOps system)
    

**Marketplace subscription:**
-----------------------------

* Delete AWS account in nOps wouldn't change the status of Marketplace Subscription.
    
* Customer should go to AWS console in order to unsubscribe nOps [https://console.aws.amazon.com/marketplace/home](https://console.aws.amazon.com/marketplace/home)
    
    

**When the client deletion queue task is executed, it would:**
--------------------------------------------------------------

* Deletes all data fetched from AWS API.
    
* Deletes all cost data ingested to nOps.
    
* Deletes client from the list of clients.
    
* Keeps the invoice generated for that client.
    
* Delete all Personally Identifiable Information associated with the client, including e-mail addresses, user names, and any other PII.**:**
    

For more information on our Privacy Policy please visit here: [nOps Privacy Policy](https://nops.io/privacy-policy/)