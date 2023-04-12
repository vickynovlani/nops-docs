---
title: SSO Integration
parent: Single Sign-On (SSO)
grand_parent: Getting Started
nav_order: 1
layout: default
---

{: .no_toc }
How to Integrate SSO in nOps
============================

Running a secure cloud system is very important. With the new nOps SSO feature, integrating SSO from your favorite SAML 2.0 provider is a smooth and easy process. You can currently integrate [Okta](https://www.okta.com/integrate/), [OneLogin](https://www.onelogin.com/product/sso), [Azure Active Directory (Azure AD)](https://docs.microsoft.com/en-us/azure/active-directory/) amongst others.


1. TOC
{:toc}

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
    

|     |     |
| --- | --- |
| Map this Attribute value | To this Attribute name |
| Email | User.Email |
| First Name | User.FirstName |
| Last Name | User.LastName |
| Groups | User.groups |

When you are done, you will be provided setup instructions which you will then use to configure SSO on nOps.

Configuring SSO on nOps
-----------------------

After setting up SSO with your SAML provider, configure SSO on nOps.

To do that, you need some key credentials from Okta or OneLogin (i.e. your provider). They are:

* Issuer URL (entityId)
    
* SAML 2.0 Endpoint (HTTP) (singleSignOnService: URL)
    
* X.509 Certificate
    

Copy these values and paste them in their respective input fields on the nOps SSO settings page shown below.

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088411/8bd0367e752c7949948fce57/UG0y1-E97C9ObGMnrU5wfeytNUircHWotayHK3ObZRKxqdLpf-p7PUyaK-N6UTo5QzBdMK99XULdhy-HON4j5a8LQPDyRgG-nqrBHbudfCToeFXpG_UA1Vxc40p4QurqZGS5Q260%3Ds0)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088411/8bd0367e752c7949948fce57/UG0y1-E97C9ObGMnrU5wfeytNUircHWotayHK3ObZRKxqdLpf-p7PUyaK-N6UTo5QzBdMK99XULdhy-HON4j5a8LQPDyRgG-nqrBHbudfCToeFXpG_UA1Vxc40p4QurqZGS5Q260%3Ds0)

**Assigning Users**

After completing these steps, you can add existing users to your application. New users will need to complete a one-time email activation in order to have SSO enabled for them.

Additional Features
=======================

nOps has some new features that you can activate for your SSO integration.

Enable SSO Login
----------------

When you enable the **Enable SSO Login** toggle shown below, users will be redirected to the SSO login for authentication the next time they try to sign in and will only need to provide their email to Sign in to nOps.

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088418/b19a55e2dc2fb670484b4c65/ex9_mHB7DVstNUlKMdDJ8Vn0E-mzMkGOjbeOlOZFCUh7uUICQdIOWNgm4l11xw-UIG0bVyGWPqTQaO_q6QJhaPSgoeu2mkvgaD8EaDF6CyCKC685J4OjankBB0nVPZVrhtdxwaH0%3Ds0)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088418/b19a55e2dc2fb670484b4c65/ex9_mHB7DVstNUlKMdDJ8Vn0E-mzMkGOjbeOlOZFCUh7uUICQdIOWNgm4l11xw-UIG0bVyGWPqTQaO_q6QJhaPSgoeu2mkvgaD8EaDF6CyCKC685J4OjankBB0nVPZVrhtdxwaH0%3Ds0)

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088426/9966dc5ef6ba59cf73e23fbd/qe85qESzlx3Op-dAAxuRpaU-L3kdjXoo-s4E8Il9GNpKfyxwadZV3rlCGsagcs9H5dVTMxAaiZGrsfyuDzt_EjWkI0nIQK7tmz57ncQ3yVVUKXMVb9wncBwMLTTedH-zpvLcz5-C%3Ds0)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088426/9966dc5ef6ba59cf73e23fbd/qe85qESzlx3Op-dAAxuRpaU-L3kdjXoo-s4E8Il9GNpKfyxwadZV3rlCGsagcs9H5dVTMxAaiZGrsfyuDzt_EjWkI0nIQK7tmz57ncQ3yVVUKXMVb9wncBwMLTTedH-zpvLcz5-C%3Ds0)

Leaving this feature disabled will require users to log in with their current login password credentials. However, this is only possible for users who went through the nOps sign-up process.

Enforce SSO login
-----------------

To enforce SSO login for **all** users, you must specify a domain in the input box and also select the **Enforce SSO login for all domain users** checkbox shown below.

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088431/9da9d2c0cb105e079cf10b43/yqUDWW6noBbckCoxHxLe7nVy4btObpjQv-n3ZbPHq8FhuWR9Nyczjxl_6w60w-XJ9yyThuROHkBXQhpjhZNKPLtKTs5C3r3IdTk0TSYoMndgQx9f_RCEz0WEgkpRqh1cjkzDt-A1%3Ds0)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088431/9da9d2c0cb105e079cf10b43/yqUDWW6noBbckCoxHxLe7nVy4btObpjQv-n3ZbPHq8FhuWR9Nyczjxl_6w60w-XJ9yyThuROHkBXQhpjhZNKPLtKTs5C3r3IdTk0TSYoMndgQx9f_RCEz0WEgkpRqh1cjkzDt-A1%3Ds0)

Users coming from the specified domain address, _must_ use the SSO Login process to sign in or they will be denied access.

If you however want to login from another domain name, you can copy the value shown in the _Shareable Link for IDP Login_ and sign in using that.

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088441/e472d12ef29542468686b003/2Kq20N6a8wVOi57t4xfZTBqvF0sE4C4eOj1mDqGLF3uD1EuSa7QiLJ607I7I57z7HAR9KG59-XGQpjiSPPm4qvJjSV3LbHViF6MbT8sTEyI56XO11DXe-mxYLmtjG-9a2N-qozaA%3Ds0)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088441/e472d12ef29542468686b003/2Kq20N6a8wVOi57t4xfZTBqvF0sE4C4eOj1mDqGLF3uD1EuSa7QiLJ607I7I57z7HAR9KG59-XGQpjiSPPm4qvJjSV3LbHViF6MbT8sTEyI56XO11DXe-mxYLmtjG-9a2N-qozaA%3Ds0)

Setting User Roles
------------------

This feature allows you to choose a default role for users. You can choose between:  
\- _client-member_ and _client-admin_ if you are using the Client nOps portal

OR  
\- _partner-member and partner-admin_ if you are using the Partners nOps portal.

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088443/76a161a9fe9dc42cde3beaa6/Ql7Di2L5NBk500k5FCjasx3XYk2Wlq7knPc0l1XUDVl3RGycQiyLEqFPI2LkKDobANefNNqIGX4N_XCeP7jg6C0itqbFTrumhIx3Nz7vD-wNPcuYu6tg21IVzs3YKaLV1DW-BM3l%3Ds0)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088443/76a161a9fe9dc42cde3beaa6/Ql7Di2L5NBk500k5FCjasx3XYk2Wlq7knPc0l1XUDVl3RGycQiyLEqFPI2LkKDobANefNNqIGX4N_XCeP7jg6C0itqbFTrumhIx3Nz7vD-wNPcuYu6tg21IVzs3YKaLV1DW-BM3l%3Ds0)

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088445/361b0b500fa83e32809f5182/QO45rsbHbA8vaF3nXwONjHpvM05cuUSS3RuNyVUGvEgm-1_FbaQ4IsUF0GDx5L5Afh1JJ2_q_uj7U2P-tgGsfBF1mYPdutJFDa4-_G8IXKIh_tjvWlao532mINBhDxt5y-mYEMLq%3Ds0)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088445/361b0b500fa83e32809f5182/QO45rsbHbA8vaF3nXwONjHpvM05cuUSS3RuNyVUGvEgm-1_FbaQ4IsUF0GDx5L5Afh1JJ2_q_uj7U2P-tgGsfBF1mYPdutJFDa4-_G8IXKIh_tjvWlao532mINBhDxt5y-mYEMLq%3Ds0)

**For the Partner portals**: the _partner-admin role_ can send invitations, configure SSO and access the partners’ clients. A _partner-member_ role has limited access only to clients.

**For the Client portal:** the _client-admin_ role has access to all available options including SSO while the _client-member role_ has **no access privileges** to the Settings pages.

Control your SSO user groups
----------------------------

You can also **control your SSO user groups** by ​​setting an nOps role based on the SAML group. This feature is currently only available for Okta.

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088448/320d3034cc99a0283a16e956/0ATIUWKq5lMbXEKeE9QZqUhWcTG4fqAXCpxkt71vcV3jMICqYXka3TMVdVs9NBqDYqXIhmEe5LgSsmeOZjq5CQeViVLjGKnzgqGHyBlr8d6JdEU60b6S0zc9sDWqdSjq__xAmjlW%3Ds0)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088448/320d3034cc99a0283a16e956/0ATIUWKq5lMbXEKeE9QZqUhWcTG4fqAXCpxkt71vcV3jMICqYXka3TMVdVs9NBqDYqXIhmEe5LgSsmeOZjq5CQeViVLjGKnzgqGHyBlr8d6JdEU60b6S0zc9sDWqdSjq__xAmjlW%3Ds0)

To enable this feature, you need to specify at least one value for admin and user groups.

In addition, you can also select the **_Allow SAML Group Configuration to Override nOps Role_** checkbox. This will give preference to _nOps defined roles_ over that of your specified provider’s roles.

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088451/d39e60a45b224ba9525ba349/oz2FGrdpRbMWqYA4c9pYOhH9Dge5-EA8wAw4QsegqPWF_Y9_C73HX1fusldJsJtSbrGKO4VRGBBHWV17Hg9LrCyxVY-TLW5NixC7CeHgQfD8r7hZu284pnHqu_VndT3r9szyaBmK%3Ds0)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088451/d39e60a45b224ba9525ba349/oz2FGrdpRbMWqYA4c9pYOhH9Dge5-EA8wAw4QsegqPWF_Y9_C73HX1fusldJsJtSbrGKO4VRGBBHWV17Hg9LrCyxVY-TLW5NixC7CeHgQfD8r7hZu284pnHqu_VndT3r9szyaBmK%3Ds0)

Update or Delete SSO Configuration
----------------------------------

Lastly, you can update your SSO configuration or delete it entirely.

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088455/d3704aac96fbc5126bfd95ad/oIVeLj_swy-uGcEW721YIIYY8ebGMLsrvYSxdBepeQI1n4w3CS2Qc3Uv-YUDMNPL_d6acDf-S31zy3fs_CrATsEPq9mnwvEDGAE5sif6TJ2oShP-iYuSM9ivIfXRkV59y2bpMts_%3Ds0)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/383088455/d3704aac96fbc5126bfd95ad/oIVeLj_swy-uGcEW721YIIYY8ebGMLsrvYSxdBepeQI1n4w3CS2Qc3Uv-YUDMNPL_d6acDf-S31zy3fs_CrATsEPq9mnwvEDGAE5sif6TJ2oShP-iYuSM9ivIfXRkV59y2bpMts_%3Ds0)

**_Note that deleting your SSO integration is irreversible. You cannot undo the deletion._**
