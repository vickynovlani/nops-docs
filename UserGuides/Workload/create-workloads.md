---
title: Create Workloads
parent: Workload
grand_parent: User Guides
nav_order: 1
layout: default
---

# Create Workloads

### Describes how to create a workload ###


## How to Create a Workload ##
========================

Workloads in nOps help you to group different AWS resources that have been created within your AWS environment. This makes it easier to carry out various assessments on those specific services that make up with _Workload_. These are the steps to create a workload in nOps.

Access **Workloads** by clicking Workloads from the tabs.

Creating a workload is as easy as selecting the **Workloads** tab and clicking the **Add New Workload** button on the top right. Once a workload is created you can edit it to add or remove resources. Note that you **_cannot_** rename a workload, but you can always create a new one.

### What to know before you begin ###
-----------------------------

nOps offers the following review types and compliance frameworks

**Review Types**

*   Well Architected Framework Review (WAFR)
    
*   Foundational Technical Review (FTR)  
    Software as a Service (SaaS)
    
*   Serverless.
    

**Compliance Frameworks**

*   HIPAA
    
*   SOC2
    
*   CIS
    

### Creating Your First Workload ###
----------------------------

If this is the first time you have created a workload, you will click “**Create new Workload**” in the middle of the screen. After that, the **Create new Workload** button will move to the top right of the window.

**To Create a new Workload**
----------------------------

1.  Click the **Create New Workload** button to create a new workload. This opens a dialog with a form to fill for creating the **_Workload_**
    
2.  Enter the following information:.
    
    *   **Workload Name** - This is an unique identifier for your workload.
        
    *   Select the **Review types** you want to use to asses this Workload. Select **Well Architected** for AWS Cloud accounts
        
    *   Select the **Compliance Frameworks** for this workload from the list. This setting is optional.  
        
    
    [![](https://downloads.intercomcdn.com/i/o/478876013/f77df4982dab99979b475588/image.png)](https://downloads.intercomcdn.com/i/o/478876013/f77df4982dab99979b475588/image.png)
    
3.  If you are using an AWS account select the toggle to change the choices and to allow nOps to find your Resources and save the WAFR compliance progress. Select an **AWS Account** and an **Environment** type and enter a **Description** for the Workload .
    
    [![](https://downloads.intercomcdn.com/i/o/478876569/96cf77a7c84549a1d076c16f/Screen+Shot+2022-03-11+at+7.56.19+AM.png)](https://downloads.intercomcdn.com/i/o/478876569/96cf77a7c84549a1d076c16f/Screen+Shot+2022-03-11+at+7.56.19+AM.png)
    
4.  **Specify the Workload resources** Enter all Regions that nOps will pull resources from. This defaults to All.  
    The **AWS Managed Services** that nOps will include in your workload. This defaults to All Managed Services and  
    Enter **VPCs** that contain the resources that nOps will include in your workload.  
    
    [![](https://downloads.intercomcdn.com/i/o/478877807/a701503a758ab7d248d83446/image.png)](https://downloads.intercomcdn.com/i/o/478877807/a701503a758ab7d248d83446/image.png)
    
5.  **Select tags** to be assigned to the resources you want to include, e.g., “ApplicationA.” You can add as many tags as you need.  
    
    [![](https://downloads.intercomcdn.com/i/o/478878322/5dce017e4a6c91a5575ead88/image.png)](https://downloads.intercomcdn.com/i/o/478878322/5dce017e4a6c91a5575ead88/image.png)
    
6.  Add notes for the workload and click **Save** to save and create this workload.
    
    And that's it!
    

It may take a few minutes for the Workload to appear. The workload is displayed on the **Workloads Dashboard**.

Click on the workload to view the details.