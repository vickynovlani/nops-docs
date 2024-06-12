---
title: EventBridge Integration for Essentials
keywords: savings, recommendations, scheduler, essentials, eventbridge
tags: [essentials, scheduler]
sidebar: mydoc_sidebar
permalink: essentials-eventbridge-setup.html
folder: Essentials
series: [Essentials, Scheduler]
weight: 1.0
---

# EventBridge Integration Guide for nOps Essentials #

This guide aims to facilitate the technical understanding and operational procedures associated with the integration of EventBridge within the nOps platform, ensuring efficient automation and management of cloud resources.

## Introduction ##

Amazon EventBridge facilitates the creation and management of event-driven applications. It is instrumental in automating and managing a variety of nOps features. nOps provides two types of EventBridges: Scheduler and Essential. The Scheduler EventBridge handles tasks related to resource scheduling, resource rightsizing, and managing idle resources. The Essential EventBridge, on the other hand, is specifically tailored for tasks like migrating storage from Gp2 to Gp3.

## Prerequisites ##

Before setting up an EventBridge, ensure:

- You have access to a nOps account.

- Your AWS account is properly configured with nOps.

## Creating EventBridge from nOps Essentials Features ##

EventBridge can be initiated from the Settings/Integration tab, from the Essential scheduler Create Window, or through recommendations in features like EC2 rightsizing, idle instances, and storage. 

![](https://lh7-us.googleusercontent.com/T-iyZVdIT4YSA2djxUVVzlWHRGp1AeY0YNvTZuJUYiBPIJhy2VaNLMxaUQJbvBIc_8ShK4UEtM0zczVukUJWAOuSk1o74BtCM6_olAKFA7K767lSr0ip1PRM45BHpmrx6GJVbEUSiRukveQyuQY4i1s)

## Creating an EventBridge When None Exists ##

If no EventBridge is associated with the client, a "Create Now" option will be available on the scheduler page of every Essentials feature. Clicking this will open a window where you can enter details such as the EventBridge name, AWS account, and region.

![](https://lh7-us.googleusercontent.com/QhwllzIt8ydRqeMUT2izQUtYdaNrxZpI9KJ1hGnCo391sENPxvbJLA1lLcR1c9ZjbKQGm60nmVf4oC7cAL50BM69R2DQWEAz3M5HI9EjmDqjE8oTnI40kjYTlRPztT7BTP97gsko9mJay0Zfz1Cz8FI)

## Configuring an EventBridge When It Exists, but Isn't Configured ##

If an EventBridge has been created but not configured, a "Configure Now" option will be visible. 

![](https://lh7-us.googleusercontent.com/ONtNjo5vV_goXn9NZemsueNPbVH5FzRGydvh-kfDTRY5Fx0rGx1X029djzCL6-dZYfxvqdKZJOYwjPwKSRcSum722c6tFus447qHYQs0fKCtYxNL_rGA-9cyimlzW6wxIH5SSsQROiISc8Kz23B3jN0)

Selecting this will display a window with details of the existing EventBridge, allowing you to configure it by launching the stack from this window.

![](https://lh7-us.googleusercontent.com/igQzjvxwOdbzqWZREtyOVTkLbjymUMy9vMDabZLXg65nafInkJWy6fKmXS2KrfZCpWqQCAJOM2avJ8QY1xhazYRybwtVU6CHH3JpFPkem6H0o7iuvWDCrlnJ6kRJCnO-e4cyISnGQrupm1C_ckvMoF0)

### Logging into AWS and Launching the Stack ###

Once you create an EventBridge, log into AWS and launch the stack from the schedule creation page. Complete the setup by clicking on "Create Stack".

![](https://lh7-us.googleusercontent.com/mUHO2IXj4C708LJxAPcVvZnMejzaWbyEGTYC0PQwUOt6wFh7aHe_QSrinam9brVVY8Cu9aI5pmQL4t4w-_4ISSc2pisIZ8fYhW7f7utM6UXy8v5RSV5ObHcbnsbHn9UsNyqZ5bEXTY0r-OLZikcc8fY)

### To Create EventBridge from nOps Integrations ###

- Navigate to "Personal Settings" and select "Integrations".

- Access the "EventBridge" tab.

- Use the "Create New EventBridge" button to either create a new EventBridge or to check the status of existing ones.

- Log into AWS and click on "Launch Stack" to initiate the stack run.

### Creating EventBridge for Multiple AWS Accounts ###

nOps supports the creation of EventBridge for multiple AWS accounts simultaneously. In the "Create New Event Bridge" window, select multiple accounts from the dropdown to configure EventBridges across several AWS accounts at once.

![](https://lh7-us.googleusercontent.com/NgqptOG06zJcGOOp3dcVQ-jmEzFWCTkUmUdYgHv1kTEtJkalZieemnXdo_2oBerihVFNLUe_SNosAxFE8fNkP2G0btUV0kc-_U2BZW56OZqcFFRaPYTsIgvVtcPLDiiuESdQY3sHI3v77T0qdIgTWbU)

Initially, their status will be "Not Connected," but you can configure them by clicking "Launch Stack". 

**For configuring all EventBridges at once, refer to the CF "**[**one-click**](https://docs.google.com/document/d/1lOijtMGlkfLrI44hgfBNLMwGhbIxIKoseZV7JcIR4L0/edit?pli=1#heading=h.v9zz7k2ypp23)**" configuration guide.**

**Updating EventBridge Status After Stack Creation**

After the successful creation of the stack in AWS, return to the nOps platform and click the "Refresh Status" button on the EventBridge to update its status from "Not Connected" to "Connected."

![](https://lh7-us.googleusercontent.com/TEQmNDZyzGKVyPnQGyQCsqmy_hIeNfRGy7FC_hrTMjBkRUnbwEVqMafL4RO3De2D0Y3gzTxIEzv8x6nP68qNXRu8obgvMrDz0yIbl-eC05bRsDAavvXH1_4AGH7Pg4PJgBCvemaIFFjR3bdQ9b9Fcmk)



<br/><br/>

{% include custom/series_related.html %}
