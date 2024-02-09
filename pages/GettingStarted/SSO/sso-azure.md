---
title: Azure SSO Integration
keywords: sso, setup, onboarding
tags: [onboarding, sso]
sidebar: mydoc_sidebar
permalink: sso-azure.html
folder: GettingStarted
series: [Onboarding, SSO]
weight: 2.0
---
## Azure SSO Integration ##

While implementing SSO (single sign on), we recommend opening 2 browser tabs. In one tab open and log into your nOps account, in the other open your Azure account. You will need to copy information from one application to the other in order to sync the information and to allow SSO access with Azure.

This topic is for Clients who log in using an Administrator Role. It assumes that you have nOps configured on your [Microsoft Entra ID](https://portal.azure.com/#home) (This was formerly known as Azure AD).

To Set Up SSO on nOps
---------------------

1.  Login to nOps and navigate to **Organizational Settings** from the profile link.  
    Or as a Partner Admin role click on the SSO link.
    
2.  From the Settings panel click the **SSO** option.
    

If you do not have SSO configured you will see a dialog to enable it

1.  Click **Enable SSO** to go to the **SSO Settings** page.
    
2.  Enable the **Enable SSO Login** toggle.
    
3.  From the **Select SSO Type** drop-down, select **Azure**.
    

Now you need to add an SSO configuration on the Azure portal.

To Set Up SSO on Azure
----------------------

1.  Login to the Microsoft Azure portal and click the **Azure Active Directory** widget to go to the **Overview** page
    
2.  Click **\+ Add** and select **Enterprise Application**.
    
3.  At the **Browse Azure AD Gallery**, search for **SAML toolkit** and click the icon when it’s displayed.
    
4.  At the **Azure AD SAML Toolkit** dialog enter a **Name** for this application and press enter. This may take a few minutes to save.  
    Suggestion for name: **nops-SSO**  
    
    After the name is entered you will be taken to the **Overview** page to continue to set up this application.
    

Assign users and groups and set up the single sign on (SSO)
-----------------------------------------------------------

1.  Begin assigning users by clicking the link in **1\. Assign users and groups** widget.
    
2.  At the **Add Assignment** page click **\+ Add** **user/group** from the toolbar.
    
3.  Click **None Selected** link and at the **Users** dialog enter search criteria to find and add users.
    
    The system may identify users that you can select.
    
4.  Click on the user/s to add them.
    
5.  At the **Add Assignment** page, click the **Assign** button to add the users you selected. You will see a success dialog and return to the **Users and groups** page.
    
6.  Once you have completed adding all users click the **Overview** tab in the left pane.
    

Set up the single sign on (SSO) widget
--------------------------------------

1.  Click the **Get Started** link in the **2\. Set up single sign on** widget.
    
2.  At the **Single sign-on** page select the **SAML** widget to open the **SAML-based Sign-on** page
    
    You will configure URLs and attributes by copying the information from nOps and pasting it into theBasic SAML Configuration page in Azure.
    
3.  From **Basic SAML Configuration** click **Edit**, then click **Add identifier**.
    
4.  Replace the **Identifier (Entity ID)** field with the **Entity ID** url from the nOps SSO page
    
5.  Replace the **Reply URL (Assertion Consumer Service URL)** with the **Assertion Consumer Service URL** from nOps
    
6.  Replace the **Sign on URL** in Azure with the **Shareable Link for IDP Login** url from nOps.
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/470977253/7f70ec59bc3118b0895f978a/A5yZYagWUUpEJbobPQChTML6YPPn-ZTasWBYcn00U2awelJFTgqWpyNQ91waaUlfXhzekG9N4peDvk48xU_sDn4aEgBCpXPme6DXs0WW9K4lB7_4avX3lKxyYC543JbOXIi32pfH)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/470977253/7f70ec59bc3118b0895f978a/A5yZYagWUUpEJbobPQChTML6YPPn-ZTasWBYcn00U2awelJFTgqWpyNQ91waaUlfXhzekG9N4peDvk48xU_sDn4aEgBCpXPme6DXs0WW9K4lB7_4avX3lKxyYC543JbOXIi32pfH)
    
7.  Once you are done click the **Save** icon on the top left corner of the dialog.
    

Return to the Sign-on page to add attributes.
---------------------------------------------

1.  Click **Edit** on the **Attributes and Claims** widget to add attributes.
    
2.  On Attributes & Claims dialog click **\+ Add new claim** to open the **Manage claim** dialog  
    You will add 3 new claims. You must enter mandatory information for **Name**, **Source** and **Source Attribute** as seen in the following table. Save each claim before you add the next one.
    


| **Name** | **Source** | **Source Attribute** |
| --- | --- | --- |
| User.FirstName | Attribute | user.displayname |
| User.LastName | Attribute | user.displayname |
| User.Email | Attribute | user.mail |

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/470977262/50a8c6d989a72ed4e2947c55/OX5Zgl3auYYDawRGK4CMh1TnrgFhJEThvIunGncxJH9_xzVXPQ3xVtl3tRIMaGSlxPgc2-9iAMKdoZzHnU3enKA5jCTZiS3dkltuYtX5Bh7a7A50YD5M0UwUGRvIa-QPFVLQ8zvm)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/470977262/50a8c6d989a72ed4e2947c55/OX5Zgl3auYYDawRGK4CMh1TnrgFhJEThvIunGncxJH9_xzVXPQ3xVtl3tRIMaGSlxPgc2-9iAMKdoZzHnU3enKA5jCTZiS3dkltuYtX5Bh7a7A50YD5M0UwUGRvIa-QPFVLQ8zvm)

3\. Click **Save** to complete the configuration for the Azure portal

Entering information from the Azure portal to nOps
--------------------------------------------------

To complete the set up, copy the following items from the Azure portal to the nOps SSO page.

1.  From the SAML-based sign-on page navigate to section **3** the **SAML Signing Certificate** widget and click the **Certificate (Base64) download link**.
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/470977264/270685a8b097e5dd6be8479f/d6In6T8KaVBKIkFGQoh6UeX82hFFPRMUQ_qV6Xw5aI5EldAei4yEaB4ImgCsRAj1MY1C98-d9S7imk0LbJo1XAT1BWBUihkdHWGRRjrznBLbJf_8e2EM6sJy44lcxoNKaw3wmxS4)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/470977264/270685a8b097e5dd6be8479f/d6In6T8KaVBKIkFGQoh6UeX82hFFPRMUQ_qV6Xw5aI5EldAei4yEaB4ImgCsRAj1MY1C98-d9S7imk0LbJo1XAT1BWBUihkdHWGRRjrznBLbJf_8e2EM6sJy44lcxoNKaw3wmxS4)
    
2.  When it is downloaded, open the download with a text editor such as NotePad (DO NOT USE WORD) and copy the contents of the certificate to the nOps **X.509 Certificate** field.
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/470977265/bdbda1cfcefd082d2e01ea5f/54ifMnFnZVN62lMnPqb5soAmiEvEaSwE2c9Jut_ru6ETD8qzEVXQyLKx15OiVIsKmxh4aD0KqwwZGb71WPXTnzeqD9q9GvSOr2PalIQrKkeSM8H5FisDQkii56_-DHRM-YfKOejB)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/470977265/bdbda1cfcefd082d2e01ea5f/54ifMnFnZVN62lMnPqb5soAmiEvEaSwE2c9Jut_ru6ETD8qzEVXQyLKx15OiVIsKmxh4aD0KqwwZGb71WPXTnzeqD9q9GvSOr2PalIQrKkeSM8H5FisDQkii56_-DHRM-YfKOejB)
    
3.  From section **4** in the **Azure SAML Sign-on** page copy the **Login URL** into the **SAML 2.0 Endpoint (HTTP) (singleSignOnService: URL) in nOps.**  
    Use this information to enter info the Issuer URL (entityId) field in nOps.
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/470977266/c74b32ff0b9b81660f270322/JczXNi-NV-bm-1-KEF1i9T-O6O0Klcf9wsbrbo5NdE6OBpIxqnjCwUXQ1em5ggu9Ol9rZmXK8KUO6FU2VK1hLtf45qoblgLvJmGGH-hJqai0ECLGV8ul0QxRIEWfYBTJinC9l4aj)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/470977266/c74b32ff0b9b81660f270322/JczXNi-NV-bm-1-KEF1i9T-O6O0Klcf9wsbrbo5NdE6OBpIxqnjCwUXQ1em5ggu9Ol9rZmXK8KUO6FU2VK1hLtf45qoblgLvJmGGH-hJqai0ECLGV8ul0QxRIEWfYBTJinC9l4aj)
    
4.  Copy the **Azure AD Identifier** URL into the nOps **Issuer URL (entityId).**
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/470977267/4aeb5713db52169bda1bc167/CDCtK1fdBZcPALzmxKMfpKgybddB4cF4CJ-A9j7YGkfKKNse6d3U_pOygIsTw9jFcZupK5Ud7GQ7P9-5-t5b9pzo4yAnjXqjccdX57qwAS8TNSWMy58hl9-48hKNXkJCPDZa5xnD)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/470977267/4aeb5713db52169bda1bc167/CDCtK1fdBZcPALzmxKMfpKgybddB4cF4CJ-A9j7YGkfKKNse6d3U_pOygIsTw9jFcZupK5Ud7GQ7P9-5-t5b9pzo4yAnjXqjccdX57qwAS8TNSWMy58hl9-48hKNXkJCPDZa5xnD)
    
5.  In the **nOps SSO** dialog navigate to **User Roles/Groups**. For **Default role** select **client-admin** to apply this role as a default for all users logging in from the Azure portal.
    
6.  Click **Setup SSO Configuration** to complete the setup.
    
    You have now completed the SSO set up on both nOps and on the Microsoft Azure portal.
    

Test your Set-up
----------------

You can now test your setup.

1.  From the Azure portal Saml-based Sign-on page click the **Test** button in section **5**.
    
2.  At the **Test single sign-on** dialog click the **Sign in as current user** and click **Test sign in**.
    
3.  Navigate to the nOps webpage to see that you are being signed in through the Azure single sign on.
    

To create and add a Group configuration
---------------------------------------

1.  Click the **Single sign-on** tab in the left pane.
    
2.  **Click + Add a group claim** to add a group.
    

You will need to enter some advanced options for this claim.

1.  At the **Group Claims** dialog select **Source Attribute: Group ID**
    
2.  Then click the **Advanced options** link.
    
3.  Click the **Filter groups (preview)** checkbox and enter information for the 3 fields:  
    Attribute to match: **Display name**  
    Match with: **Contains**  
    String: **nops**  
    The _string_ should match the name of the group you entered.
    
4.  Check the **Customize the name of the group claim** box
    
5.  Enter the Name for the attribute as: **User.Groups**
    
6.  **Save** the Group Claim
    
7.  Return to the Single sign-on tab. You should see **user.groups** added to the **User Groups** setting in Attributes and Claims section
    

Add the group to the Azure portal.
----------------------------------

1.  Click on the Home in the breadcrumb links at the top of the page.  
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/470977269/94eb4bd7075b3aa304f2773e/MjDChB9hNUNqXHWVVUabUOb_fqjtqnOKjMrCXnfQRh5NyNmPDSP0JZBMz7TCWI9NXxZwy0OZvJvOWouV7pYeQIu4UTCN00-UV5oLnUxukPaFEmY_GbuAVUf9MVosrwwuJ_DkDENs)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/470977269/94eb4bd7075b3aa304f2773e/MjDChB9hNUNqXHWVVUabUOb_fqjtqnOKjMrCXnfQRh5NyNmPDSP0JZBMz7TCWI9NXxZwy0OZvJvOWouV7pYeQIu4UTCN00-UV5oLnUxukPaFEmY_GbuAVUf9MVosrwwuJ_DkDENs)
    
2.  From the Home page find and click **Groups**.
    
3.  At the **Groups | All groups** page click **New group**.
    
4.  For **Group name**, enter a name containing the String you entered earlier (nops). For example nops-group
    
5.  Click **Create** to return to the **Groups | All groups** page. And refresh the page to see the group you added. You can also search for it.
    
6.  Copy the **Object ID** for the group and enter it in the **nOps SSO** page under **User Roles/Groups** \> **Client Admin Groups** field.
    
7.  Ensure that the **Set nOps role based on SAML Group** toggle is enabled.
    
8.  Then click **Update SSO Configurations**.
    

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/470977272/f32a736f3abe5aaebac3eb43/HvqyjTMGFbrRJtKgpSizpRAiau76bRdlgDuNcO1RMRhmpC3vs566nt9Jn1uztnpxRLfjL8E32cFrlKjfyBOco4rt0WL6nm0myhMo067OdcIEStXNYJJVNZhZdjzJWZNaqMiSg-pH)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/470977272/f32a736f3abe5aaebac3eb43/HvqyjTMGFbrRJtKgpSizpRAiau76bRdlgDuNcO1RMRhmpC3vs566nt9Jn1uztnpxRLfjL8E32cFrlKjfyBOco4rt0WL6nm0myhMo067OdcIEStXNYJJVNZhZdjzJWZNaqMiSg-pH)

To test this group integration where a member of a group is automatically logged in as an Admin user.

1.  Return to the Home page in Azure Portal.
    
2.  From My Apps, select the **Nops App** you added and click on it.
    

You are directed to the nOps Web app login page and are automatically logged in since SSO was set up from the Azure portal.

<br/><br/>

{% include custom/series_related.html %}