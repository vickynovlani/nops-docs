---
title: SSO Integration
parent: Integrations
grand_parent: Integrations and Agents
nav_order: 6
layout: default
---

{: .no_toc }
SSO Integration with nOps
===========================

1. TOC
{:toc}

How to Integrate SSO in nOps
----------------------------

Running a secure cloud system is very important. With the new nOps SSO feature, integrating SSO from your favorite SAML 2.0 provider is a smooth and easy process. You can currently integrate [Okta](https://www.okta.com/integrate/), [OneLogin](https://www.onelogin.com/product/sso), [Azure Active Directory (Azure AD)](https://docs.microsoft.com/en-us/azure/active-directory/) amongst others.

Getting Started
---------------

To incorporate SSO in nOps, you need to configure the SSO for your SAML provider. To do that, you first need to get some credentials from your nOps dashboard.

Your nOps Credentials
-------------------------

1.  To access your **nOps SSO credentials**, navigate to your SSO Settings Page. Go to:  
    _Organizational Settings > SSO_ if you’re using the client portal  
    or _Partner Settings > SSO_ for the partner portal_._  
    You will be prompted to enable SSO for access to the **SSO Settings** page.
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088389/e338e1b86d912955fdf49105/n1jcayCRuXrQ03DVw7w81lDC9trilJHOUmk92Cwmahm9BCPHw9HyfwVPttpoDSdEt76vvwqTzluBzDQXV3dLv5vI5Scs3PjAgHCiWQ7lbz2xDpVIGGcAe3gaVaexZ6VPCVUoRsCF%3Ds0)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088389/e338e1b86d912955fdf49105/n1jcayCRuXrQ03DVw7w81lDC9trilJHOUmk92Cwmahm9BCPHw9HyfwVPttpoDSdEt76vvwqTzluBzDQXV3dLv5vI5Scs3PjAgHCiWQ7lbz2xDpVIGGcAe3gaVaexZ6VPCVUoRsCF%3Ds0)
    
2.  Copy the _Assertion Consumer Service and Entity ID_ values on the SSO Settings page and paste them into your SAML provider’s SSO configuration settings.
    
    [![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088403/9f8126203b09d03792360f4e/LSG4YJ9OpA8xf1SW6B2hN-tv7y9vTHHRZjHUTjpp1g7NGdL8tEZ4Aj96BiarTzqKI5EDW9ayC5L4NJDjh6CENFwDpe_Lgity6QnHzBtamXARXPlC3V-SFhSHpVMYwSx-Dqscemmh%3Ds0)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088403/9f8126203b09d03792360f4e/LSG4YJ9OpA8xf1SW6B2hN-tv7y9vTHHRZjHUTjpp1g7NGdL8tEZ4Aj96BiarTzqKI5EDW9ayC5L4NJDjh6CENFwDpe_Lgity6QnHzBtamXARXPlC3V-SFhSHpVMYwSx-Dqscemmh%3Ds0)
    
3.  Next you need to map some defined attributes. This should be done using the exact values as described. These attributes are called “Parameters” in OneLogin.
    


| --- | --- |
| **Map this Attribute value** | **To this Attribute name** |
| Email | User.Email |
| First Name | User.FirstName |
| Last Name | User.LastName |
| Groups | User.groups |

When you are done, you will be provided setup instructions which you will then use to configure SSO on nOps.  
  
To learn how to configure SSO, see the full [configuration documentation](../GettingStarted/SSO/configure-sso).