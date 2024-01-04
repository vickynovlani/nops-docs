---
title: AWS SSO Integration
keywords: sso, setup, onboarding
tags: [getting_started, onboarding, sso]
sidebar: mydoc_sidebar
permalink: sso-aws.html
folder: GettingStarted
series: [Onboarding, SSO]
weight: 1.0
---


# How to use AWS SSO for nOps #


In the nOps platform, [navigate to the SSO Configuration settings](https://app.nops.io/v3/settings?tab=SSO) to enable SSO

Within AWS:
1. Navigate to **IAM Identity Center** -> **Applications** -> **Add Application**
    ![](/tmpimg/select_app.png)

1. Choose Custom application
1. Add custom SAML 2.0 application
    ![](/tmpimg/configapp.png)


1. Add your application name and description.


1. Copy the information from AWS to the nOps SSO settings:

    _AWS_: IAM Identity Center SAML issuer URL
    _nOps_: Issuer URL (entityId) and SAML 2.0 Endpoint (HTTP) (singleSignOnService: URL) 

    _Example_: https://portal.sso.us-east-1.amazonaws.com/saml/assertion/XXXXXXXXXXXXXXXXXXX


1. Copy the following information from nOps to AWS:

    _nOps_: Assertion Consumer Service
    _AWS_: Application ACS URL

    _Example_: https://app.nops.io/sso/v1/YYYYYYYYYYYYYYYYYYYYYYYYY/?acs

    _nOps_: Entity ID
    _AWS_: Application SAML audience

    _Example_: https://app.nops.io/sso/v1/YYYYYYYYYYYYYYYYYYYYYYYYY/metadata

1. In AWS, download the IAM Identity Center Certificate and copy the certificate content to the nOps X.509 Certificate section


1. Go to the **IAM Identity Center Applications** settings
    ![](/tmpimg/addusers.png)
1. Click on Actions -> Edit Attribute mappings.


    |**application** | **Maps** | **Format** | 
    |-------|--------|---------|
    | Subject | ${user:subject} | emailAddress |
    | User.Email | ${user:email} | basic |
    | User.FirstName | ${user:givenName} | basic |
    | User.LastName | ${user:familyName} | basic |










