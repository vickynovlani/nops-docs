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

**Steps to configure Azure SSO integration with nOps**

Note: We suggest that you keep both the AWS and nOps platform open in the same browser to switch between during the steps. 

1. **Create an Enterprise Application inside Microsoft Entra ID**

- Within your Azure portal, Navigate to **Enterprise Applications → All Applications → New Application**

- Fill in the name of your app (For example, “nOps SSO”)

- Keep the default option **Integrate any other application you don't find in the gallery (Non-gallery)**. 

- Click **Create**

![](https://lh7-us.googleusercontent.com/XziDUqi_SWuakPwExwOs--0qsDkEJHiQ9hhUF1ubRCLNXN6BkbmjBo3J2drnsI_RC4EmlMckxrTcn2VoYM819xyx_pcASBO7jFBRo1-pmbniTbyn7FEa-CT1iwUqYG60tRK1IXjXLE7T99oPaaa88jU)

2. **On the nOps platform, navigate to Organizational Settings → SSO to Enable SSO and Select SSO Type: Azure**

![](https://lh7-us.googleusercontent.com/KAjsV5lwDczUsAZoeSTDO2n6Ud7_rETTzDcqTnwohOMJQODU7Sch4w_VJbEjJ89310CsuEObWQ4hqgFeqDyv7M1hFTBuojcJ0n8jKneMNMjFdDalR6UL2i1Xke2HZdrcFwEDFiIQnZCEm_EklVfUI_o)

3\.  **Perform the following steps on the Azure Portal where Enterprise Application creation is in progress.**

- In the getting started section, click **Setup Single sign on**

- Select **SAML**

- Edit **Basic SAML Configuration**

- Copy the **Entity ID** from **nOps SSO integration Details** and paste it into the **Azure Portal** **→** **Enterprise Application** **→** **Basic SAML Configuration** field **Identifier Entity ID.**

* Copy the **Assertion Consumer Service URL** from **nOps** **SSO Integration Details** and paste it into **Azure Portal** **→** **Enterprise Application** **→** **Basic SAML Configuration** **→ Reply URL (Assertion Consumer Service URL)**

- Copy the **Shareable Link for IDP Login** from **nOps SSO integration Details** and paste it into **Azure Portal → Enterprise Application → Basic SAML Configuration** → **Sign On Url.** 

- Save the details

![](https://lh7-us.googleusercontent.com/_4Xb6q9ZF6pWMgSLV0PceLaWAYZAdsZvF8ZK4iKHQjm6vSEy73E6D1erKiJKl-9fa-TL99xH85jjYPQTChcIwNO5iU62BLkyeA9Wz4_UPamTM-Utr2jikuAko-LpEeV_7lDgJ5mqEzq7USMLpIvz8bo)

- Copy the **Login** **URL** from **Set up nOps SSO** and paste it into the **nOps platform** **→** **SAML 2.0 Endpoint (HTTP) (singleSignOnService: URL)**

* Copy the **Microsoft Entra Identifier** from **Set up nOps SSO** and paste it into the **nOps platform** **→** **Issuer URL (entityId)**

****![](https://lh7-us.googleusercontent.com/0kJur031_ZUn1-nMic6Raf-mgSPKz6qfzol4L4UV0JngMP_l8J5JgHXenftpYjKFcFuG5AhQqIaH_gCDkYaTcttAIAH1k8EH-Gy4FyQ3zZMnZ5aIh4k9kN3JIkxYWMhfh-syqXOqdqH7MyH9gCgW7fU)****

4\.  **Download the IAM Identity Certificate.**

- Switch to the **Azure Portal** and download the **Certificate (Base64)** provided in the **SAML Certificates** section.

- Open the downloaded Certificate into a text editor such as Notepad.

- Copy the Certificate data and paste it into the **nOps platform** **→** **Organization Settings** **→** **SSO** **→** **Your** **SSO** **Details** section field: **X.509 Certificate**

![](https://lh7-us.googleusercontent.com/q_Tc3F28yLFnx78Sd7E_A0OFpm6ZJNIviUzbqG5W5P1gtBNX5gQzQSRgz6c3okGO6ZaEod5iMR7r39akQpXU_G14tyhpZpUsjbrnshlXe82luUiPinL3pLmab-qAfsfCY7X8JlR3hyBzjy_-pbFadDg)

5\. **Navigate to Attributes & Claims:  Configure Attribute mappings**

- Click on the **Add new Claim** button. You will need to add 3 new claims in the **Manage claim screen** with providing **Name**, **Source** & **Source Attribute**.

|                |            |                      |
| -------------- | ---------- | -------------------- |
| **Name**       | **Source** | **Source Attribute** |
| User.FirstName | Attribute  | user.displayname     |
| User.LastName  | Attribute  | user.displayname     |
| User.Email     | Attribute  | user.mail            |

![](https://lh7-us.googleusercontent.com/Eqq5JPbsAb8sWxsjT2evMUmUgHYWpBtC77CMzfI4ehSsd_NBMCwL4HM-ADgqGxyAUPXkpll1X8PGcs-tCQiYjSpHZi6QyvW4Sgoo_peBNYx0Kme6XoAezeeVosqdEQkq61LxdOWU8931buMValTyBPc)

**Note :** The namespace field must be blank, if you are editing existing attributes make sure to delete the namespace.

6.  **Provide Default roles in the nOps platform.**

- Navigate to **Organization Settings** **→** **SSO** and select **Default roles** for your User/Groups

- Click on **Setup SSO Configuration**

![](https://lh7-us.googleusercontent.com/qcJwTvq2qnWGDOj1F5SMGQGnZXNzYW13YTu8Ofz9GzR565Jwoknj8KuM6vj8Ta0pZo7NTISPTjEoRVndoHOB_9ceI0fVxIfz1KAHS8vmcUq_tn1xXsGkQ2xxlM9UwwGr3aQOYhEEQTRn8uGX6m31bhs)

7\. **Switch to Users and Groups to Create Groups and Users, and assign them in the nOps SSO Application.** 

- Navigate to **Users and groups** in the left panel.

- Add a new user/group or select an existing option from the list

8\. Go to **Test single sign-on with nOps SSO** and click **Test sign in.**

9\. A confirmation email should appear on your Microsoft email portal. Click to confirm and allow access.. ****

![](https://lh7-us.googleusercontent.com/fnVPI91efAIAlp9bg6j1j2pSX5FMOxCvKvkSnBwx5UYUBBqCHSPG1mh4gCFjKLPTN94aojgsNkfekWTQTCBeXk6VttSjqYOaunBSoMddJ2sP7aKZYjO-8JErLOFR8ijYbOzmtSjajkH0wUug9Gbmz9g)

Email Copy

****![](https://lh7-us.googleusercontent.com/NccBlI06WaxlrDw5bR9fmoShy2I67aM9nWhXdwJodGp0bPBi-rCt9J7KrwiKOsr_AaEnf2egFvVDUtdRR5mDtRaGnwito6xNYDe5yp8VdULjg6tR3uh8wg26YmQgYzGfVndosqKCzej8QiU7Bqngb4A)****

**Retry Test single sign-on with nOps SSO and click Test sign in. You should now be able to log into your nOps account.** 

****


<br/><br/>

{% include custom/series_related.html %}