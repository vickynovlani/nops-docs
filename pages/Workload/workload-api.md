---
title: Workload API
keywords: reporting, assessment, compliance
tags: [compliance, reporting]
sidebar: mydoc_sidebar
permalink: workload-api.html
folder: UserGuides
---

# Workloads API Documentation #
===========================

_API token generation_ Go to settings -> API Key menu item

Click **“Generate API Key”**

![](/tmpimg/gen-api.png)

Copy the key you’ve have.

To use the nOps API, you will need to append your query string in the following manner: [https://app.nops.io/nops\_api/v1/some\_endpoint/](https://app.nops.io/nops_api/v1/some_endpoint/)_?api\_key=&lt;YOUR\_API_KEY&gt;_

**_List workloads_**  
/nops\_api/v1/workload/?api\_key=&lt;API_KEY&gt;

![](/tmpimg/list-workloads-api.png)

**_Get specific workload data (with answers data) by its ID:_** /nops\_api/v1/workload/&lt;WORKLOAD\_ID&gt;/?api\_key=&lt;API\_KEY&gt;

![](/tmpimg/workload-data-api.png)

**_Get WA summary for a specific workload_** /nops\_api/v1/workload/&lt;WORKLOAD\_ID&gt;/rules\_summary/?api\_key=&lt;API_KEY&gt;

![](/tmpimg/waf-summary-api.png)

**_Get a budget for a specific workload_** /nops\_api/v1/workload/&lt;WORKLOAD\_ID&gt;/budget/?api\_key=&lt;API\_KEY&gt;

![](/tmpimg/budget-api.png)

**_List attached resources for a specific workload_** /nops\_api/v1/workload/&lt;WORKLOAD\_ID&gt;/resources/?api\_key=&lt;API\_KEY&gt;

![](/tmpimg/wl-attached-resources-api.png