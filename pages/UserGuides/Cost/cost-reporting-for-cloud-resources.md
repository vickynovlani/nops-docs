---
title: Cost Reporting for Cloud Resources
keywords: cost reporting, cost history, cost allocation
tags: [cost_visibility, reporting, savings]
sidebar: mydoc_sidebar
permalink: cost-reporting-for-cloud-resources.html
folder: UserGuides
---

# Cloud Resources Cost - Stay on Top of Cost Changes #


Choosing _Cloud Resources Cost_ from the Cost Control pull-down gives you a set of tabs that show your cloud spend broken out by:

*   **Cloud Accounts** - spend by account in AWS, Azure, etc.
    
*   **Regions** - spend by region in cloud vendor
    
*   **Cloud Services** - spend by service in each cloud vendor
    
*   **Resources** - spend from cloud resources being used
    
*   **Non-resources** - spend not specifically from cloud resources
    
*   **Usage Types** - spend by AWS _usage type_
    
*   **Operations** - spend by AWS operation
    
    * * *
    
*   **Tags** - spend by tagged resource, with tagged resources grouped under key name
    
*   **Change Management** - log of daily cost changes
    

The first seven of these tabs (Cloud Accounts, Regions, Cloud Services, Resources, Non-resources, Usage Types, and Operations) each give you:

*   A **Spend Summary** at the top :
    
    *   **Yesterday's Total Spend**
        
    *   **Last Week's Spend**
        
    *   **Month to Date Spend**
        
    *   **AWS Credits** (applicable tabs only)
        
    
*   An array of **Filters** in the vertical box at the left, enabling you to view cost trends over time, and to understand which resources contribute to higher costs.
    
*   A **History** bar chart just below the Spend Summary. Note the two buttons above the right side of the chart:
    
    *   **See Spend Forecast**
        
    *   **See Spend History**
        
    
*   Details of **Daily Spend** listed in a table below the History chart
    

**Spend Summaries**
-------------------

A few notes:

*   The periods for the Spend Summary boxes _Yesterday_, _Last Week_, and _Month to Date_ are as defined by AWS.
    
*   If you choose a specific **date range** in the Filters box at the left, the Spend Summary becomes just the total spend for that date range (no yesterday's spend, last week's, or month to date).
    
*   On the **Resources** and **Non-resources** tabs, the Spend Summary gives the appropriate _subtotals_ for resources or non-resources. For the other five tabs, the Spend Summary gives the same overall totals. (The History chart and Daily Spend table below the Spend Summary do give details broken out per the specific tab title.)
    
*   **Credits:** The overall credits value in the spend summary is as reported by AWS, and includes both AWS _credits_ and _refunds_. The number in the Credits box of the Spend Summary is for the specific date range in the Filters box at the left. The credits value in the summary when you hover your cursor over a "circle-_i_" is the portion of the AWS credits plus refunds, reported by AWS, for _yesterday_, _last week_, or _month to date_, depending on the box.
    
*   **Hover text** summary: Hovering your cursor over the "circle-_i_" in any of the three Spend Summary boxes gives the Resources, Non-resources, and AWS Credits value for the time period of that box (yesterday, last week, month to date). These numbers and the associated time periods are as defined in AWS.
    

### **Filters** for Analyzing Costs ###


The **Filters** vertical box at the left allows you to zero in on a combination of resources and parameters and so find the sources of cost trends over time, or understand which resources contribute most to higher costs. 

Filtering criteria you've chosen are shown by ovals above the Spend Summary, so that you can easily track the filtering criteria that you have in effect -- _however_, note that any custom date range is not represented by an oval above the Spend Summary.

The Filters box includes a **calendar tool**, which allows you to **specify a date range** for which costs are to be displayed and summed. When specifying a custom date range:

*   Use the **Apply** button at the very bottom of the enlarged calendar tool, to make your date range take effect
    
*   Note the "easy-button" pre-specified date ranges, like **_1W_**, **_3M_**, or **_May 2022_**, just above the Apply button.
    

The default cost display might only cover the preceding month. The calendar tool can be used to view cost changes over time periods that are meaningful to your business.

![](/tmpimg/calendar-select.png)

Spend figures next to regions, cloud-managed services, and other criteria listed in the Filters box are the total for that filter criterion and will match the total in the Daily Spend table on the page.

### **History Chart** ###


The color-coded choices beneath the chart can be clicked to exclude each from the chart, enabling you to focus on particular regions, services, resources, etc.

### **Daily Spend** ###


*   The Total column in the table is the total for the date range set in the Filters box on the left.
    
*   The table of daily values scrolls left to right through the days (scroll bar at bottom) and is paginated 10 records per page (page selection at lower right).
    
*   The Daily Spend detail on each page has a **Download CSV** button at the upper right that downloads _all_ spend records for that page. For example, if a tab such as Operations has 170 records, the default view may display only 10 records at a time. However, clicking the download icon will download **all** records (in this example, 170) in a .csv file:
    

**Non-resources**
-----------------

This tab gives costs not associated directly with a resource, such as taxes and AWS or Azure services (for example, AWS Key Management Service, or AWS CloudTrail). To see a complete list of your non-resource costs for the selected filter criteria (including selected date range in the Filters box calendar tool), click **Download CSV** at the top of the Daily Spend table below the History bar chart.

Cost Details for Resources and Non-resources
--------------------------------------------

You can get details for any Daily Spend value or Total value in the Resources or Non-resources pages by clicking on the value:

![](/tmpimg/See-Details.png)

![](/tmpimg/Displayed-Details-on-Resources-and-Non-resources.png)

Tags
----

The **Tags** tab gives the spend for all tags by key name. Note that:

*   To see the spend for each _value_ under a key name, expand a key name by clicking on it, or by clicking on > at the right end of the row.
    
*   To see detailed costs for tag key-value pairs, use the Tag Explorer page under Cost Control (**Cost Control** pull-down, choose **Tag Explorer**).
    
*   A blue **Download** button (upper right) gives you a CSV file of the spend figures by key name, for all keys. The CSV does not break out by key value.
    
*   The **Cost (total)** column gives the total spend for the time period specified in the Filters column at the left -- default, 1 month to date.
    

Change Management
-----------------

The **Change Management** tab lists the changes in your account and the potential billing impact of these changes. You can expand or collapse each day's list of changes by clicking the down arrow at the right, and you can click on the **Daily**, **Weekly**, or **Monthly** filter options to see the total spend change over daily, weekly, or monthly intervals for each resource type. Change the **Sort by** options to view increases or decreases by cost or by percent.  

![](/tmpimg/change-mng-filter-sort.png)

Finding Cost Changes
====================

Use one or a combination of the following methods to explore cost changes, compare what you paid this month vs last month, or investigate a spike in costs.

*   **Check costs on the dashboard.** From the Dashboard, navigate to **Cost Control** / **Cloud Resources Cost.** Check the Cloud Accounts, Cloud Services, Resources, and Operations spends. Spend numbers flagged in red show are higher than in the previous time period. Check for variances. You might notice (for example) that unexpectedly higher costs stem from adding a number of new resources.
    
*   **Use the calendar tool.** For example, in the **Resources** tab, if the spend and usage look normal and there are no spikes, use the calendar tool to include costs for the prior month. This may show changes in resources. Also examine **Non-resources** tab to see how such items as support costs, usage costs for pausing and restarting an instance, egress costs, or tax costs are contributing to your spend.
    
*   Also in the **Resources** tab, use the various filters in the box at left – for example, to isolate key resources by tags, region, account, usage type, etc., so that you can evaluate a specific resource or a set of resources for changes in cost over time.
    
*   From the **Regions** tab, click on **See** **Spend Forecast** to see estimates based on your current spend.
    
*   **Set up Notifications.** From the Change Management tab click on **Subscribe** to be notified of cost changes. You can select a period of time, and a range for the cost comparison (by week or by month). Enter emails for people who will receive these notifications.