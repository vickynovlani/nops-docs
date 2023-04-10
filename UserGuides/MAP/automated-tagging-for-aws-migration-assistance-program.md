---
title: Automated Tagging for AWS Migration Assistance Program
parent: MAP
grand_parent: User Guides
nav_order: 2
layout: default
---

{: .no_toc }

# Automated Tagging for AWS Migration Assistance Program #

If you're participating in AWS's Migration Assistance Program, you probably know that getting AWS credits for resources that you've migrated into AWS requires that you apply the right tags to those resources – and you want to apply those tags as early as possible in order to earn the credits as early as possible. nOps MAP features help automate this process, ensuring that you get the right tags applied to your resources as early as possible and get the maximum credit from the MAP program.

These MAP features can aid you if you're a new AWS customer, just starting out with AWS and migrating your workloads into the AWS cloud, or an existing AWS customer moving workloads from on-prem data centers or from other cloud providers.

And note that qualifying for the credit also requires an AWS Well Architected Framework Review, so that you get the most from your cloud deployment – and that review is also facilitated by nOps tools.

- TOC
{:toc}

nOps Automated Tagging for MAP-Program Credits
==============================================

In order to get your AWS MAP credits, all your resources must be tagged according to the MAP rules. If your resources are not tagged properly, you won’t get the credits – and credits will only accrue on spends that occur _after_ the tags are applied. nOps helps you to list the resources migrating for your various workloads, identify those that have yet to be tagged, apply the right tags, and then track your AWS incentive credits over the course of your migration. And in so doing, you'll be setting up all your workloads for the required Well Architected Review, which nOps can also help you conduct.

To use the nOps MAP facitliy, from the nOps dashboard go to **Workload > AWS MAP:**

[![](https://downloads.intercomcdn.com/i/o/569897785/a11b1550480de171e7cbccf6/2022-08-26_21-39-57.png)](https://downloads.intercomcdn.com/i/o/569897785/a11b1550480de171e7cbccf6/2022-08-26_21-39-57.png)

Defining Your Migration Projects
--------------------------------

The nOps MAP facility starts with the page **_AWS MAP 2.0 Summary_**, where you’ll find three sections:

* **QTD (Overall Migration Resource Spend Summary)** – gives quarter to date total spending in AWS on migrated resources (tagged and untagged), untagged resources, and earned MAP credits.
    
* **Your Current Tagging Status** – shows the % of your migrated resources are tagged with _map-migrated_ in order to get credits, and what % are untagged. It also shows the resource spend equivalent to the percentages.
    
* **List of Migration Projects** – shows projects that you’ve defined. Each project corresponds with a _MAP Migration Contract_ from AWS and is identified by the project number in that contract, of the form _MPExxxxx_ (where _xxxxx_ are digits).
    

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311785/8e2b893458b376924f8f78b7/chDGJ-Q931vYOaZNTN2piisd_TiRnmHfCJznXReoY79yrJwn5U9pCBNkMiR1witAOZkrCzrkdVsbcThfvEEppe0Yf4a0ow29eitIKGxyyLfHjfTrdJnMeV0aeI6s2AgwI-wnMoWmeaESovsPEDqNrYg)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311785/8e2b893458b376924f8f78b7/chDGJ-Q931vYOaZNTN2piisd_TiRnmHfCJznXReoY79yrJwn5U9pCBNkMiR1witAOZkrCzrkdVsbcThfvEEppe0Yf4a0ow29eitIKGxyyLfHjfTrdJnMeV0aeI6s2AgwI-wnMoWmeaESovsPEDqNrYg)

To create/add a MAP migration project in nOps, click **\+ Create MAP Project** at the upper right; it will bring up this dialog:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311796/8041917409406949cc51d05f/fha5TuMYE7Z3TniRfaAAS2p0BIHTZsoGPg1JoZxNv-PPCoj6EsIDWTBvH77AKb97FSHsfpzx5gytHruD4sRzOO7BgMwB8h5opz2Xc0USLnt74zqiOw2Jni_YLLTt0W6ozDxMDSv7RB4N2WlzWfJUY70)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311796/8041917409406949cc51d05f/fha5TuMYE7Z3TniRfaAAS2p0BIHTZsoGPg1JoZxNv-PPCoj6EsIDWTBvH77AKb97FSHsfpzx5gytHruD4sRzOO7BgMwB8h5opz2Xc0USLnt74zqiOw2Jni_YLLTt0W6ozDxMDSv7RB4N2WlzWfJUY70)

In the dialog, fill out the details:

* **Project Name —** Choose one that is meaningful to you.
    
* **Project ID —** The project ID starts with “MP” followed by 5 digits (_MPExxxxx_, where _xxxxx_ are digits). If you are not sure where to find your MAP _Project ID_, refer to the top of the first page of your MAP contract.
    
* **_Start Date_** and **_End Date —_** They should be per your MAP contract terms from AWS.
    
* **Tag Key —** Prefilled for you.
    
* **Server ID —** Must be the _exact_ server-ID string from AWS. If you do not already have an AWS server ID, click the blue **_Generate Server ID_** button, which will take you to the AWS facility for creating one – be sure and copy the ID that you create there in order to come back to this dialog and paste it into this **Server ID** field.
    
* **Workload (optional) —** As identified in nOps’ Well Architected Framework Review facility. You can select an existing workload that you’ve created in nOps or you can create a new workload for the MAP project. To create a new workload, click **Create Workload,** this will take you to the **_Workloads_** page in nOps. With workloads, you have the option to define a scope for where nOps should look for tagged and untagged resources.
    

Once you’ve entered all the details for this MAP project, click **Create.** The project you just created will show up in the **List of Migration Projects** on the **_AWS MAP 2.0 Summary_** page:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311803/8ecc57533661244a974df60f/pLdmHASUA-NwjsCreguPIeK-TCy0eiJtMV9SSc0ppdTHVEkd_5j2PFEUl_u-7jwho8KT1GG10GW7Ngoc9sWnetpBebtVp356VA2Q-7mRHxtVIm10FuBjNA1Bi10xqmREwSnkI9KqkGkow2T5xRJukAQ)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311803/8ecc57533661244a974df60f/pLdmHASUA-NwjsCreguPIeK-TCy0eiJtMV9SSc0ppdTHVEkd_5j2PFEUl_u-7jwho8KT1GG10GW7Ngoc9sWnetpBebtVp356VA2Q-7mRHxtVIm10FuBjNA1Bi10xqmREwSnkI9KqkGkow2T5xRJukAQ)

Every MAP project that you create this way in nOps will correspond to a MAP _Migration Contract_.

* * *

**Note:** Creating a migration project will not tag the resources of that project. To tag resources, continue to the next section, “Tagging Resources”.

* * *

Tagging Resources Within Each Project to Earn MAP Credits
---------------------------------------------------------

nOps provides an easy automated way for you to tag any untagged resources.

Once your MAP migration projects are defined, each with its associated resources via the server ID, nOps will show you all the AWS resources associated with the servers you have identified for the migration projects. As more and more resources from the servers/storage units are added, you will periodically come back to nOps to tag all untagged resources.

To tag resources of a project:

1.  Click ➡️ in the **Action** column of the **List of Migration Projects** section:  
    This will take you to the **Migration Details** of the migration project.
    
2.  Scroll down to the **List of resources** section. This list contains all the resources associated with the migration project:
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311812/ed5cac57642199d7cd2411ea/rqrNZT_HNkLspQutUWbN7GgsRbAbKF5tiRQXzMMHStgbcPrcHHBXKNIPfbIlktdPw1SceLaYy-co5o52vJgxcKoE_ts13xAw0SuCVtvk6-3R-zUjo2os5jYTSiux2kXPzSFbAa92CdcQdlt7_uNI2e4)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311812/ed5cac57642199d7cd2411ea/rqrNZT_HNkLspQutUWbN7GgsRbAbKF5tiRQXzMMHStgbcPrcHHBXKNIPfbIlktdPw1SceLaYy-co5o52vJgxcKoE_ts13xAw0SuCVtvk6-3R-zUjo2os5jYTSiux2kXPzSFbAa92CdcQdlt7_uNI2e4)
    
3.  Select the resource(s) you want to tag, and click **\+ Add Migration Tag** and then **\+ Tag Now**:
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311819/d8ef78d840173f3fc83500e9/IQZK_9xrnRd-TZsSNgqlcQupepLOTcYWth9vl4VLoCX3Z58N0WMzwIfq-hdYs1SqrMI1oS0KTnmXlscBGmyF-RIoJqSI2s42ML38PM7XOX3lGQw1tAXb4wx3c50fmXcAg27pHV2-ncO0YCLcoqtqw1Q)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311819/d8ef78d840173f3fc83500e9/IQZK_9xrnRd-TZsSNgqlcQupepLOTcYWth9vl4VLoCX3Z58N0WMzwIfq-hdYs1SqrMI1oS0KTnmXlscBGmyF-RIoJqSI2s42ML38PM7XOX3lGQw1tAXb4wx3c50fmXcAg27pHV2-ncO0YCLcoqtqw1Q)
    
4.  Click **Yes**:
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311826/b69d7238732ad42c5ef0c863/A5GNkEqH877xaAtCQAlkX-9DSubonqZ09bosRPevvgaFLHqS9YW52fGgg1X5cTvGXwSs1cK9h83NXwcwDaT4ZXP2sw1Vwavx-bAi9lQ1pZrR7QeDSsFQ5VwVLEeELMMdOwB8PA2BYDhibXMB4bVce7s)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311826/b69d7238732ad42c5ef0c863/A5GNkEqH877xaAtCQAlkX-9DSubonqZ09bosRPevvgaFLHqS9YW52fGgg1X5cTvGXwSs1cK9h83NXwcwDaT4ZXP2sw1Vwavx-bAi9lQ1pZrR7QeDSsFQ5VwVLEeELMMdOwB8PA2BYDhibXMB4bVce7s)
    

* * *

**Note:**

Once you click **Yes**, nOps will redirect you to AWS, where you will tag the selected resources. nOps will pre-fill **Tag Key**, **Tag Value**, and **ARN,** which is some of the information required to tag the selected resource.

To successfully tag a resource in AWS, you (the customer) will need two permissions from your AWS Admin – permission for the selected resources and the permission to tag resources.

* * *

Managing Your Migration Projects
================================

Once you’ve defined one or more migration projects in nOps, you will see each of those projects listed at the bottom of the **_AWS_** _**MAP 2.0 Summary**_ page where you started:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311837/cd3a9bf8dc55269badbefe82/Sj_tjYY3ofokcbWBLHQiVxoiK-3BetCT1FZpuH2bKFBK_QqLh6Wsg99GYBrAbMiS_J8tQr1MV7NQgIXkOv5R1RQAO0vCPshfkQbtM94W0OpL8qYtQ--eAPxlN6A_RJrJgD808ZebmSDxmvjBHdJnsJQ)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311837/cd3a9bf8dc55269badbefe82/Sj_tjYY3ofokcbWBLHQiVxoiK-3BetCT1FZpuH2bKFBK_QqLh6Wsg99GYBrAbMiS_J8tQr1MV7NQgIXkOv5R1RQAO0vCPshfkQbtM94W0OpL8qYtQ--eAPxlN6A_RJrJgD808ZebmSDxmvjBHdJnsJQ)

You can access and manage any migration project by clicking the ➡️ button in the _Action_ column of the **List of Migration Projects** section.

In the **_AWS MAP 2.0 Summary_** page you will also find a collective summary of all of your migration projects in the form of:

* **Overall Migration Resource Spend Summary —** Shows quarter to date (QTD) migrated resource spend, untagged resource spend, and estimated credit.
    
* **Your Current Tagging Status —** Shows a bar chart for how much of your spending has been tagged and how much remains untagged in the current QTD, across all of your migration projects.
    

* * *

**Note:** Once a quarter ends and the next one starts, you can still tag the untagged resources from the previous quarter but the previous quarter’s cost will not change.

* * *

Navigate and Track Your Incentive Credits
=========================================

In the **_AWS MAP 2.0 Summary_** page, again note the arrow at the right of each migration project line, in the _Action_ column. Clicking that arrow brings up the details of that migration project:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311845/cf3a2f8abb4ebae61a52cc54/YojSUjSRrR1X7gKMjUvL3pLk_6RUaYgDOejOUtaSKeuukFkglWyyAL16wMroMFrVyYZGFj5djOpg2O858QzyJyCAoXpS_khb02PNWfqTIg2amnCmDh3QWOcLKCNVPnQEHSv9SSR6bg5KsuWHqE-z1H4)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311845/cf3a2f8abb4ebae61a52cc54/YojSUjSRrR1X7gKMjUvL3pLk_6RUaYgDOejOUtaSKeuukFkglWyyAL16wMroMFrVyYZGFj5djOpg2O858QzyJyCAoXpS_khb02PNWfqTIg2amnCmDh3QWOcLKCNVPnQEHSv9SSR6bg5KsuWHqE-z1H4)

The details page shows the performance of a specific migration project, and it is divided into four distinct sections. At the top of the details page you will see the **Migration ID**, **Start Date**, **End Date**, **Tag Key**, **Server ID**, and **Workload** associated with the migration project you just clicked:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311850/b5b0f88ed50b26b9504c7135/GMa-MkNGsv-GrQvfvywUxpFgkNTF1eF5o609En0xr6VogYWeF_yLNp7TcyYUZ7HzvxjWBDFU4CAYZPu2Y-j1TmUiZ4IdKZR2bH8fjT1J1TpYOfhqM7MZ_VQHL0BktzWAPM6Luhnwb65ajKczeBCFpfo)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311850/b5b0f88ed50b26b9504c7135/GMa-MkNGsv-GrQvfvywUxpFgkNTF1eF5o609En0xr6VogYWeF_yLNp7TcyYUZ7HzvxjWBDFU4CAYZPu2Y-j1TmUiZ4IdKZR2bH8fjT1J1TpYOfhqM7MZ_VQHL0BktzWAPM6Luhnwb65ajKczeBCFpfo)

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311856/317ab0aeda807dc865f4d74f/T-qLfrRxLZv7I1dPqTdzBtgFHZRxXMOw1tXo2OHFO2RIo3CnfVOHHJTfA3U0V0ion-1GLj-FHNuYNeI3xd8gfJaYjZGMrz_voS4tD5RiaidktO-Q68A875xuAV2svwSwYrYHgvb-KeS-jkcMW1qrfgI)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311856/317ab0aeda807dc865f4d74f/T-qLfrRxLZv7I1dPqTdzBtgFHZRxXMOw1tXo2OHFO2RIo3CnfVOHHJTfA3U0V0ion-1GLj-FHNuYNeI3xd8gfJaYjZGMrz_voS4tD5RiaidktO-Q68A875xuAV2svwSwYrYHgvb-KeS-jkcMW1qrfgI)

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311861/1fa556b09ed2a12ae003703b/R6X7BSdLyCU2fetWVswgII08qELwKlJ-TgaOy1DeyI_8coaRYv-pbAtTAH2yDW8Gd89b_zDpSr_ODOcdamYyWOmE2J246RaMiko5kh2UQ_yRJZg5Pnf1YDmxeWHkHR4USwFU-S7VIfysAy0dkXzIYRc)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/557311861/1fa556b09ed2a12ae003703b/R6X7BSdLyCU2fetWVswgII08qELwKlJ-TgaOy1DeyI_8coaRYv-pbAtTAH2yDW8Gd89b_zDpSr_ODOcdamYyWOmE2J246RaMiko5kh2UQ_yRJZg5Pnf1YDmxeWHkHR4USwFU-S7VIfysAy0dkXzIYRc)

The next three sections are all about navigating your incentive credits, tracking your tagging status, and tagging untagged resources:

* **MAP Tracker**
    
* **Your Current Tagging Status**
    
* **List of Resources**
    

MAP Tracker
-----------

MAP Tracker offers a way for you to find the scope of your project and navigate your incentive credits over the entire period of your migration, with the help of:

* **MAP Spend:** Total Spend/Cost excluding CUR line-item types Tax, Credit, and Refunds.
    
* **Trailing Twelve Month (TTM) MAP Spend: Sum of MAP spend in the existing quarter and the previous three quarters.**
    
* **General Spend Growth:** Refer to the _MAP Credit Calculations_ section of your AWS MAP plan.
    
* **Multiply by 25%**: 25% delta value of General Spend Growth.
    
* **Earned MAP Incentives:** Credits that you have earned from AWS with the MAP plan.
    
* **MAP Credits Disbursed:** Credits that you have received from AWS. You only receive your earned credits in the month after a quarter ends.
    
* **Cumulative MAP Credits Disbursed:** Cumulative sum of all past quarters and the current quarter (-) MAP credits disbursed.
    

Current Tagging Status
----------------------

This section is similar to the Current Tagging Status of the **_AWS MAP 2.0 Summary_** page_,_ which summarizes the tagging status of all your migration projects.

The Current Tagging Status on this details page shows the tagging status for only this specific migration project. It shows a bar chart for how much of your spending has been credited against tagged resources, and how much remains against untagged resources, in the current QTD, for this specific migration project.

List of Resources
-----------------

This section shows all the resources, tagged or untagged, within the migration project. You can filter the resources based on the account associated with the resource and the tagging status (tagged, untagged) of the resource. You also have the option to search any specific service with the help of the search box at the top right of the list.

To tag untagged resources, select the untagged resources and click the **\+ Add Migration Tag** button. To learn more about the process in detail, see the [Tagging Resources Within Each Project to Earn MAP Credits](https://docs.google.com/document/d/1lxEdILiJPMnq8Mp1knY7DmmRnWBzCsE-pRZqi3JeymY/edit#heading=h.6o1okpkboq8l) section of this article.

The resource table gives:

* **Service Name — AWS service that contains the resources.**
    
* **Resource Name — Resource associated with the AWS service.**
    
* **Account — The AWS account associated with the resource.**
    
* **Region — Region of the resource.**
    
* **QTD Cost — Quarter to date cost of the resource.**
    
* **Action —** Click the _Action_ to see the _Details_, _Cost History_, and _Config History_ of the resource.
    

The resource table will update periodically as more resources are added. Continue visiting the **List of Resources** section to tag all newly added untagged resources for the duration of the migration project.

* * *

**Note:**

Once you tag an untagged resource, it will take approximately one hour for the change to reflect in nOps.

You can select multiple resources and tag, then click on the **\+ Add Migration Tag** button to tag them in one go. For resources that belong to different accounts, nOps will present them grouped by account, and you can tag resources for one account at a time.

* * *

Troubleshooting
===============

Matching Spend and Credit Numbers with AWS
------------------------------------------

What to do if numbers don’t match what see in AWS:

\- Check dates of tagging vs Amazon

\- Put in past dates for tagging when not tagged till later in AWS

\- Vs Tag Explorer, which assumes the resource had the tag for the history of its life

AWS Logins for Generating Server ID and for Tagging Resources
-------------------------------------------------------------

What to do if you don’t have the permissions to tag your migration project resources:

* Ask your AWS admin to grant you permissions.
    
* Check if you have the permissions for the resource that you are trying to tag.