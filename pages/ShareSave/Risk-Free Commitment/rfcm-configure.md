---
title: Configure Risk-Free Commitment Management
keywords: savings, recommendations, sharesave
tags: [savings, recommendations, sharesave]
sidebar: mydoc_sidebar
permalink: rfcm-configure.html
folder: ShareSave
---

## ShareSave Configuration ##
=======================

In the scope of this document, we will go through the configuration of **ShareSave -  Risk-Free Commitments**.

To learn about **ShareSave - nSwitch Resource Scheduler** and its configuration, see [Utilize nOps nSwitch Resource Scheduler with EventBridge Integration to Reduce Costs Automatically](solutions-using-eventbridge-with-nswitch-to-reduce-costs.html).

To configure **ShareSave - Risk-free Commitment**, follow these steps:

1.  Log in to your nOps environment and head over to the **ShareSave** dashboard:
    
 ![](/tmpimg/sharesave-menu.png)
    
2.  On the **ShareSave** dashboard, in the **List of Opportunities** section, click the **Configure Risk Free Commitment** button:
    
    ![](/tmpimg/configure-rfcm.png)
    
    1.  If your account has already been configured, or AWS Organizations have not been enabled, you won’t see the **Configure Risk Free Commitment** button. The button is only visible to new customers and existing customers who haven't configured ShareSave yet and requires AWS Organization structure.
        
    2.  _Risk Free Commitments_ are only available to customers that onboard a Master Payer Account. You will not see the button if you haven’t onboarded a Master Payer account.
        
    
3.  Once you click the **Configure Risk Free Commitment** button, the following pop-up will appear:
    
    ![](/tmpimg/rfcm-proceed.png)
    
    1.  If the pop-up does not appear, make sure that the pop-up isn’t being blocked by your browser.
        
    2.  Before you click **Proceed,** make sure that you're logged in to your AWS master account in the same browser.
        
    
4.  After you click **Proceed**, nOps will take you to your AWS console’s CloudFormation **Quick create stack** page —with all the required information pre-filled— in order to create the required Cost and Usage Report (CUR). **Acknowledge** and click **Create stack**:
    
    ![](/tmpimg/rfcm-stack.png)
    

**ShareSave - List of Risk-Free Commitments** configuration is now complete.

* * *

**Note:** It will take upto 24 hours for the data to populate in nOps.

* * *
