---
title: Tag Explorer to Manage Tag Competency
keywords: cost reporting, cost history, cost allocation
tags: [cost_visibility, reporting, savings]
sidebar: mydoc_sidebar
permalink: cost-tag-explorer.html
folder: UserGuides
---

# Tag Explorer - Manage Tag Competency

## Tag Explorer ##
============

The Tag Explorer feature allows you to assess tags you attached to resources for billing information to better organize your costs. Such as costs for different stacks, customers, environments, projects, departments, or teams. Displaying the current information will highlight untagged resources. Following are some terms and what they mean:

**Tag Key:** is top level of the tag.

**Tag Value:** you can assign more than one tag value to a tag key. For example:

*   Application: Production
    
*   Application: Testing
    

**Use Case:** Use tags to understand the cost of all the resources used to run an app. You can report on Tag Keys and Tag values. It's an easier way to group resources to view their corresponding costs

This feature is available from a Client Page.

On the NavBar click **Cost Explorer > Tag Explorer**

![](/tmpimg/tag-explorer-menu.png)

**Filter by any of the following:**
-----------------------------------

*   Date
    
*   Custom Rules
    
*   Resources Launched after
    
*   Resources Launched before
    
*   AWS Account
    
*   CloudFormation: Stack-Name
    
*   Regions
    
*   AWS Manages Resources
    
*   Operations
    
*   Usage Type
    

When hovering over the row for Tags used on the left-hand side it will breakdown the cost of each AWS managed services by color. Depending on the color of the graph line you hover over it will bring the cost of the AWS managed service to the top of the graph key.

In the **All tags list**, you can select a tag to view details. To do this click the arrow in the **ACTION** column.

![](/tmpimg/tag-click-for-values.png)

The following page displays a breakdown of the **Tag name**. From this page you can see: Service, Resource name, Project, Region, and Total Cost.

Clicking the arrow in the **ACTION** column, for details about the selected Service .

![](/tmpimg/tag-value-resource-action.png)

A pop-up dialog provides details on when the Service was created and last used.

*   Select **Add a Jira Ticket** to connect to Jira to create a ticket.
    
*   Click **View Resource on AWS Console** to navigate directly to the resource in your AWS Account.
    

![](/tmpimg/resource-jira-console.png)