---
title: Integrate DataDog with nOps Platform
keywords: savings, recommendations, datadog, essentials, rightsizing
tags: [agents_integrations, essentials]
sidebar: mydoc_sidebar
permalink: integrate-datadog-with-nops-platform.html
folder: Integrations_and_Agents
series: [agents_integrations]
weight: 2.0
---



# Steps on DataDog Side  #

- ## **Create API Keys**

1. Navigate to Organization settings in the DataDog dashboard, then click the API keys. 
2. Click the New Key button, depending on which you’re creating.
3. Enter a name for your key. I.e., “API key for nOps ”
4. Click Create API key.
5. Save API Key **(not the Key ID)** somewhere safe to use in nOps in the next phase of the document.

![](https://lh7-us.googleusercontent.com/WOhiokjX_Mv1ZwDL6KBJv22z1Bu771c_r1CbHfPHYZRJ7rGIY0n0qkecHYfP-0q4ZA6xjHqcJ1EXheclh1fVKvcKx_dRadF4pP9LlDzq0tF8YPuHmDy7_5QTM-AnXYKufJNuBlC3LeU46SRc78pUO_k)

![](https://lh7-us.googleusercontent.com/Ulu32dmnIYU7jDlYd_r1iYza5f6PdovjnNTap77A40v4pNxX0Tg6RYYNFY_Tj22Wfz9cAb1ZeCroRknNJB9SvOFGB0j3B0zkody_jwRU587gyppIGuuFeLNJBDHT79AdMISOsAA0LhPMMy-me4aXJlc)


- ## **Create Application Keys**

1. Navigate to Organization settings in the DataDog dashboard, then click the Application keys. 
2. Click the New Key button, depending on which you’re creating.
3. Enter a name for your key. I.e., “Application key for nOps ”
4. Click Create Application key.
5. Save Key **(not the Key ID)** somewhere safe to use in nOps in the next phase of the document.

![](https://lh7-us.googleusercontent.com/nepqyNK8IHmDtN3wJw1IcS6BizcbkDToPVt5_mD2ZuzOb2MQWqFbJQCAnOpjSB3kuoAtUznnBPwfyaQ8qORQLzU7U_-nGb3gGVWZSJJyMEoYwz49vJpGs-vwidWv_71JosPVGQYBGJTn5J_tpZt_6rA)

![](https://lh7-us.googleusercontent.com/VxETkxXkPWJSZYOde_tzuuoCDO6sdDsxhbOikAPFkh0q-mCw_gtbk91zmClR2BBDd1IdVkhhB6GezsI_-zuLLDBB4wZldlzN_oUQWMSU2E4AOQZ1Cm_rPiFG2OtaD_fpUph6BXrbD3W4G8KfntKn1bo)

- ## **DataDog Site Parameter**

1. Copy the site parameter from the following table or [webpage](https://docs.datadoghq.com/getting_started/site/) by matching your datadog dashboard URL, that you use to login. You can read more about it [here](https://docs.datadoghq.com/getting_started/site/).

![](https://lh7-us.googleusercontent.com/h22uhji1J3sLCuITw4uv8Z9Xj0EuSABg06tS6xXiQB9DFdvUJ9eMyOVDEauEPgktgh6Uxxr3NNvMUME3oV1nIDeZHYK_G7wgjwXtbJ5NHOKM12YOQRo1ht1DXD0XoDTxpZDy8RSU9kvcVgQbqaeIeWk)



# Steps on nOps side #

****

![](https://lh7-us.googleusercontent.com/ybJIXKsBN0OIgik_mIHk_E1eEOz3FITb2vbAkEjcGbXqDbut6ID52Qdg-gMcRStlb2mwEU6DT09f4YLn6apLFo3Cz_9szWE5QMW-RQbu0dRWTJB-XxUFu5yei8CLd1cGOfnDe_n0NWMXyRNc65vBeyM)

****

**Step 1:** Login to your nOps Client Dashboard <https://app.nops.io/v3/>  

**Step 2:** Go to the top-right corner to menu and select **_Organization Settings_**

**Step 3:** Go to Integrations from left-hand side bar and choose DataDog tab

**Step 4:** Fill in the API Key, App Key, and DataDog Site captured from previous step

**Step 5:** Hit save. 

![](https://lh7-us.googleusercontent.com/zNUIUY76pvYB9J7kYr1bSlAF3sd_Nl-2CmuRxEg5RA2g6IACZg3zk8AWRzKr3KBuyRz17-5WxlgnN63Zu3m28YznRh0cxBrT3PzyVB391j1FJRxaOnmcqaNJPATcdUCf6-_aWN_RTryC9Eh1OebAimU)


**Note:** If the instance ID is missing in DataDog,

Please make sure that DataDog can identify instance\_ids for your instances. You can check it here <https://app.datadoghq.com/infrastructure>. If that is not the case, try the following:

1. Adding this line to your DataDog agent configuration file:

    **ec2_prefer_imdsv2: true**

    <br>
    Referring to 
    https://docs.datadoghq.com/integrations/guide/aws-integration-troubleshooting/#ec2-metadata-with-imds-v2

<br/><br/>

{% include custom/series_related.html %}