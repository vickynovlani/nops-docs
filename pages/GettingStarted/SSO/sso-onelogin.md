---
title: OneLogin SSO Integration
keywords: sso, setup, onboarding
tags: [getting_started, onboarding, sso]
sidebar: mydoc_sidebar
permalink: sso-onelogin.html
folder: Getting Started
---

# How to use OneLogin SSO for nOps #


nOps supports SSO using OneLogin.

While implementing SSO (single sign on), we recommend opening 2 browser tabs. In one tab open and log into your nOps account, in the other open your OneLogin account. You will need to copy information from one application to the other in order to sync the information and to allow SSO access with OneLogin.

**This topic is for Clients using an Administrator Role.**

You will complete the following steps:


    

## Configuring OneLogin on nOps. ##


1.  Log into nOps as a Admin user and select **Settings**
    
2.  Click **SSO** on the left pane.
    
3.  At the **SSO Settings page**
    
    Enable the **SSO login** toggle
    
    Select the **OneLogin** option  for **Select SSO Type**
    
4.  Now navigate to theOneLogin app. You will return to this page to add: Issuer URL (entityId), SAML 2.0 Endpoint (HTTP) , and X.509 Certificatebfrom OneLogin.
    

## Sign in to OneLogin and set up nOps ##


1.  In a new browser tab, login to **OneLogin** and navigate to the **Applications** page.
    
2.  Click **Add App.**
    
3.  Search for **SAML Test Connector (advanced)** to find the SAML 2.0 connector and
    
    click the icon.
    
    ![](/tmpimg/ol-find-app)
4.  At the **Add Connector** dialog, you can change the **Display Name**, add an icon, and enter a description. Ensure that the **Visible in portal** toggle is turned **on**.
    
5.  Click **Save**.
    
    Once saved, you will see new tabs appear in the left pane.
    
6.  Click on **Configurations**.
    
7.  Copy the following configurations from the **Enable SAML 2.0** page in the **OneLogin** app to paste into nOps OneLogin SSO page as described in the next section.
    

| **Copy from OneLogin field** | **Paste into nOps field** |
| --- | --- |
| Issuer URL (entityId) | Issuer URL (entityId) |
| SAML 2.0 Endpoint (HTTP) | SAML 2.0 Endpoint (HTTP) |
| X.509 Certificate | X.509 Certificate |

If required, use the one line format tool to generate a certificate.

[https://samltool.com/format_x509cert.php](https://samltool.com/format_x509cert.php)

## Setup OneLogin configurations on nOps ##

1.  If you are logged out of nOps, log in and go to the **SSO** settings screen as described in [the topic](#h_35f33efe86) above.
    
2.  Paste the configurations from OneLogin into the fields in nOps as described in the last step (Step 7) of the [previous section](#h_c9a6c91daa).
    
3.  When you are done, click **Setup SSO**.
    
4.  Refresh the page to populate values for **AssertionConsumerService** and **EntityID** if they are not populated already.
    
    You will return to OneLogin to enter these 2 values.
    

## Adding Information from nOps to OneLogin ##

Now that OneLogin is set up on nOps, you need to add the nOps settings to your OneLogin configuration.

1.  On OneLogin app page setting open the **Configuration** tab.
    
2.  From the nOps page, copy and paste configuration information from:  
    **EntityId** into the **Audience** field on OneLogin.
    
3.  From the nOps page, copy and paste configuration information from the **AssertionConsumerService** into the following fields on OneLogin :  
    \- Recipient  
    \- ACS (Consumer) URL* and  
    \- ACS (Consumer) URL Validator* fields
    
4.  Click **Save** to save the settings and go to the **Info** tab.
    

## Adding Parameters on OneLogin ##

Add parameters to OneLogin so that you can sync the user names and other attributes between the two applications.

1.  From OneLogin SAML 2.0 connector page that you set up a previous section, navigate to the **Parameters** tab on the left pane. From here you will add 3 new fields.
    
2.  Click **Add new field**
    
3.  Enter field name:  
    **User.email**
    
    Check the **Include in SAML** checkbox
    
    Click **Save.**
    
    In the **Value** field enter **Email.**
    
4.  Repeat the steps by clicking **Add new field** to add a field for:  
    **User.FirstName**  
    Check the **Include in SAML** checkbox  
    In the **Value** field enter: **First Name**
    
    Click **Save**
    
5.  Repeat the steps by clicking **Add new field** to add a field for:  
    **User.LastName**  
    Check the **Include in SAML** checkbox  
    In the **Value** field enter: **Last Name**
    
    Click **Save.**
    

### Adding Users on OneLogin ###

Users added in OneLogin can be added to nOps for SSO. However you must first set up access for nOps

1.  From the OneLogin app click the **Users** tab from the top toolbar
    
2.  Click **New User**.
    
3.  Turn the **Active** toggle on.
    
4.  Enter information about the user for the: First Name, Last Name, Email, and Username fields.
    
5.  Click **Save User.**
    
6.  Navigate to the **Application** tab in the left pane and in the Application field click the + (plus) icon
    
7.  Add the SAML 2.0 application you created earlier to grant access for this user.  
    Click on the **More Actions** dropdown and select **Send Invitation.**
    
    Upon receipt a user must click the link to accept it, and to set a password.
    
8.  Later when logging into OneLogin they will see the SAML 2.0 app.
    
9.  Clicking on the app directs the user to nOps.  
    nOps sends an email requiring the user to confirm the SSO login.
    
10. Once the confirmation is received, the user is able to log into nOps.
