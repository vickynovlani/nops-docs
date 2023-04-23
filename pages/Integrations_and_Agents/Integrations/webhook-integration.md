---
title: Webhook Integration
keywords: reporting, integrations
tags: [agents_integrations]
sidebar: mydoc_sidebar
permalink: webhook-integration.html
folder: Integrations_and_Agents
---

{: .no_toc }
# Webhook Integrations 

1. TOC
{:toc}

## Configuring Webhook Integrations for 3rd party apps ##

Use nOps Webhooks integrations to notify you when a specific event, such as a violation, occurs in your AWS cloud environment.

You must be an **Admin** user to set up a Webhook.

nOps Webhooks are easy to configure, use HTTP protocols, and are extensible. They support the standard GET, POST, PUT, PATCH, and DELETE operators.

This article contains the following topics:

Before you Begin

[Configure a Webhook](#configure-a-webhook)

[Edit, or Delete a Webhook](#edit-or-delete-a-webhook)

Before you begin
================

1.  Login to nOps using an Admin role
    
2.  From the **Profile** menu select **Organization Settings** to go to the Setting pane.
    
    If you are a partner Admin, From the **Profile** menu select **Manage Clients**, select a client from the list, click the dot menu and select **Go To This Account** \> then select **Organization Settings** from the Profile menu**.**
    
3.  From the **Settings** pane click **Integrations.**
    
4.  Select the **Outgoing** **Webhooks** tab
    

What to know before you create an Outgoing Webhook
--------------------------------------------------

* Create outgoing webhooks to notify you about violations as they occur in your AWS environment.
    
* Use the **+Create Webhook** to create as many webhooks as required  
    **IMPORTANT:** All fields marked with an asterisk are required. The webhook cannot be saved without this information.
    
* We currently support the following **Event Type** and **Request Methods.**
    
    **Note**: The dialog choices change when a different **Request Method** is selected.
    



| **For Event Type** | **Select this Request Method** | **Triggered** |
| --- | --- | --- |
| New Rule Violation | POST | Anytime a new rule violation occurs. |
| Reserved Instance Surplus | POST | When a Reserved Instance surplus is detected |
| Reserved Instance Deficit | POST | When a Reserved Instance deficit is detected |

Configure a Webhook
===================

1.  From the **Integrations** page select the **Outgoing Webhooks** tab.
    
2.  Click the **+Create Webhook** button.
    
3.  At the **Create New Webhook** dialog enter a **Name** for the webhook.
    
4.  The select an **Event Type** from the available options. See the table above this section for a complete list.
    
5.  The **Request Method** field contains GET, POST, PUT, PATCH and DELETE operators.  
    To _send_ information about an event, select **POST**.  
    
    ![](/tmpimg/webhook-name.png)
    
6.  Enter the **End Point (Target URL)** information. An endpoint is the URL to which the notification will be sent. Most customers typically post to a specific Slack channel. You will need to get this URL from the target application. For example, for Slack see the following link on how to get started with [incoming Slack Webhooks](https://api.slack.com/messaging/webhooks).  
    
     ![](/tmpimg/endpoint2.png)
    
7.  Once the webhook is created, the target application provides information about the **Header** key and value pair. For example, for Slack the header and value pair are:
    
    Content-type and application/json
    
    You can add multiple Headers if required.
    
8.  The **Substitutions** table displays attributes that you can use in the **Request Body** for information about the event. Your choices are:  
 
<pre>

    {{time}} The time the event was detected
    
    {{name}} The name of the rule that was violated
    
    {{description}} Details about the event or rule.

</pre>

![](/tmpimg/substitutions.png)
    
9.  The **Request Body** contains an automatic JSON validator to check the code you enter.  
    Add or edit the text attribute to send a specific message as seen in the following example:

 ```json

    {  
      text: 'nOps detected another New rule violation. The rule {{name}} was violated at: {{time}}. Description {{description}}.'  
    }

```
For a Reserved Instance Surplus the message could be as follows:
 
 ```json
    {  text: 'nOps detected a Reserved instance Surplus in your account at: {{time}}. Description {{description}}.'}
```

10. Click **Save** to save the webhook.
    

Edit, or Delete a Webhook
=========================

Once a webhook is created, you can edit it, or delete it from the list on the **Outgoing Webhooks** tab.

* **Click the Edit icon to edit a webhook.** For example, if you need to change the endpoint location
    
* **Delete the webhook** using the Delete/Trash icon.  
    **Note:** Once a webhook is deleted the information _cannot_ be recovered.
