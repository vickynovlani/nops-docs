---
title: Data Purge
parent: Settings
grand_parent: User Guides
nav_order: 6
layout: default
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
    

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/306169838/fbc56554d1582ab1e8c90756/4yegi0VwyG_SN7QXO6S0NuULHRX5n2HCFTQoXHGEc-l4RUIDLdRUhzuKGLE47EY9gJhTM4MmFSRZmYMgNPZ6jSnwCWG70JAocG-uVQBOrmimFROAWbKmCiACf7A3QpoVaSq1X4J-?expires=1619020800&signature=fdd78313d569140af4ac98211a5a14654c541d342af2ac20bfbd903a3a243952)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/306169838/fbc56554d1582ab1e8c90756/4yegi0VwyG_SN7QXO6S0NuULHRX5n2HCFTQoXHGEc-l4RUIDLdRUhzuKGLE47EY9gJhTM4MmFSRZmYMgNPZ6jSnwCWG70JAocG-uVQBOrmimFROAWbKmCiACf7A3QpoVaSq1X4J-?expires=1619020800&signature=fdd78313d569140af4ac98211a5a14654c541d342af2ac20bfbd903a3a243952)

**When the account deletion queue task is executed:**
-----------------------------------------------------

* Deletes all data fetched from AWS API.
    
* Deletes all cost data ingested to nOps.
    
* Keeps user login (email address and password which is used to login to nOps system)
    

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/306168195/ecc5de773d640ee77bd1cd74/U2vii1drLCAUJiJIoO7VVhmE-xaC0-c6xob4DiwDpf3EBOqAAUcDG8rUQiW1o6Pd31eWl5-upy6oJkEENigu9oyfdtKNcI4m03TN_-QKg5_lCtkGYuxkCvjs5DOX0Y4qUy3OJFar?expires=1619020800&signature=681879bb902614c7b7d32ed842a421d83b2a747f04e5c919217016f92c76bd0e)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/306168195/ecc5de773d640ee77bd1cd74/U2vii1drLCAUJiJIoO7VVhmE-xaC0-c6xob4DiwDpf3EBOqAAUcDG8rUQiW1o6Pd31eWl5-upy6oJkEENigu9oyfdtKNcI4m03TN_-QKg5_lCtkGYuxkCvjs5DOX0Y4qUy3OJFar?expires=1619020800&signature=681879bb902614c7b7d32ed842a421d83b2a747f04e5c919217016f92c76bd0e)

**Marketplace subscription:**
-----------------------------

* Delete AWS account in nOps wouldn't change the status of Marketplace Subscription.
    
* Customer should go to AWS console in order to unsubscribe nOps [https://console.aws.amazon.com/marketplace/home](https://console.aws.amazon.com/marketplace/home)
    

**Delete client from nOps partner portal**
==========================================

* A partner admin can delete their client in the nOps partner portal client settings page.
    
* When the admin clicks on delete client in nOps, the client will be scheduled for deletion within 30 days.
    

**When the client deletion queue task is executed, it would:**
--------------------------------------------------------------

* Deletes all data fetched from AWS API.
    
* Deletes all cost data ingested to nOps.
    
* Deletes client from the list of clients.
    
* Keeps the invoice generated for that client.
    
* Delete all Personally Identifiable Information associated with the client, including e-mail addresses, user names, and any other PII.**:**
    

For more information on our Privacy Policy please visit here: [nOps Privacy Policy](https://nops.io/privacy-policy/)