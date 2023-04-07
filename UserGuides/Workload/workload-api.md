---
title: Workload API
parent: Workload
grand_parent: User Guides
nav_order: 6
layout: default
---

# Workloads API #


## Workloads API Documentation ##
===========================

_API token generation_ Go to settings -> API Key menu item

Click **“Generate API Key”**

[![](https://downloads.intercomcdn.com/i/o/286343453/72c024fa3bd53d786f710205/image.png)](https://downloads.intercomcdn.com/i/o/286343453/72c024fa3bd53d786f710205/image.png)

Copy the key you’ve have.

To use the nOps API, you will need to append your query string in the following manner: [https://app.nops.io/nops\_api/v1/some\_endpoint/](https://app.nops.io/nops_api/v1/some_endpoint/)_?api\_key=&lt;YOUR\_API_KEY&gt;_

**_List workloads_**  
/nops\_api/v1/workload/?api\_key=&lt;API_KEY&gt;

[![](https://downloads.intercomcdn.com/i/o/286343531/1cfcebcfd35623fd37bce975/image.png)](https://downloads.intercomcdn.com/i/o/286343531/1cfcebcfd35623fd37bce975/image.png)

**_Get specific workload data (with answers data) by its ID:_** /nops\_api/v1/workload/&lt;WORKLOAD\_ID&gt;/?api\_key=&lt;API\_KEY&gt;

[![](https://downloads.intercomcdn.com/i/o/286343568/3e276cb78c255f8567dd9493/image.png)](https://downloads.intercomcdn.com/i/o/286343568/3e276cb78c255f8567dd9493/image.png)

**_Get WA summary for a specific workload_** /nops\_api/v1/workload/&lt;WORKLOAD\_ID&gt;/rules\_summary/?api\_key=&lt;API_KEY&gt;

[![](https://downloads.intercomcdn.com/i/o/286343657/4d031eb1bc1ac44249d0d379/image.png)](https://downloads.intercomcdn.com/i/o/286343657/4d031eb1bc1ac44249d0d379/image.png)

**_Get a budget for a specific workload_** /nops\_api/v1/workload/&lt;WORKLOAD\_ID&gt;/budget/?api\_key=&lt;API\_KEY&gt;

[![](https://downloads.intercomcdn.com/i/o/286343691/5247ceb725c092602b15a418/image.png)](https://downloads.intercomcdn.com/i/o/286343691/5247ceb725c092602b15a418/image.png)

**_List attached resources for a specific workload_** /nops\_api/v1/workload/&lt;WORKLOAD\_ID&gt;/resources/?api\_key=&lt;API\_KEY&gt;

[![](https://downloads.intercomcdn.com/i/o/286343739/fbd94a2e711d3335ada2d405/image.png)](https://downloads.intercomcdn.com/i/o/286343739/fbd94a2e711d3335ada2d405/image.png)