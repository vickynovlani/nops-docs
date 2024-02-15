---
title: The nOps Scheduler API Guide
keywords: setup, onboarding, nswitch, sharesave, slackbot, developer, api
tags: [developer]
sidebar: mydoc_sidebar
permalink: scheduler-api.html
folder: Developer
series: [API]
weight: 4.0
---

# nOps Scheduler API Guide # 

## What is nOps Scheduler? ##

**nOps Scheduler** automatically pauses unused cloud resources, such as EC2 instances, EBS volumes, and RDS instances. It works by creating tag-based schedules. For example, an organization might create a schedule that pauses all EC2 instances with the tag "dev" during off-peak hours. 

nOps Scheduler provides a [RESTful API](https://app.nops.io/public_redoc/) to create, manage and monitor schedules and resources.

## Why use nOps Scheduler? ##

- **Cost optimization.** Scheduling can save organizations a significant amount of money on Dev and QA costs, especially during off-peak hours.
- **Time savings.** Lack of time and resources is a key blocker preventing engineers from reducing cloud spend — nOps Scheduler makes scheduling simpler and faster.
- **Automation**. Our AI is constantly learning your usage patterns for greater savings.

### Summary of steps ###

In order to implement grouped schedules using the nOps API:

1. Authenticate to the nOps API
2. List created nOps Scheduler
3. Create a grouped schedule
4. (Optional) Create an EventBridge
5. Get the status of the grouped schedule


## Complete instructions ##

### 1. Authentication ###

The first step is to authenticate to the nOps API. Here are the steps to create a signed request (a key pair used to verify your signature).

- **Configure an API key in nOps** through the nOps app.
- **(Optional) Create a public/private key pair.** Configure nOps with the public key to validate the signature.
- **Compose your request.**

This [article](https://help.nops.io/developer-getting-started.html) provides more detailed information on the API authentication process.

### 2. Getting nOps Schedules ###

Once you are authenticated, you can onboard resources to nOps Scheduler with this request:

    GET https://app.nops.io/svc/notifications/scheduler/nops_scheduler?api_key=<insert_api_key>

This request requires the following parameters:

- `PI <insert_api_key>`: Your nOps API key

For example, the following request would give nOps Scheduler resource recommendations:
    ![](https://lh7-us.googleusercontent.com/4_xYjjd0ed4PFw4JwMSwDAQ6h14tFqrJ2qlx2YLssH-qS7Ut0yq-HIx07jcR3WAxsYrvWBxpJWK8EMvezEwCYBdFBgo1OhLkcRxa2fKJCfqPzT6Xp8GoCwYm_1T1CDWMC1NukLkLpxvmd0QEizKQsVY)****

### 3. Scheduler Recommendations ###

Once you have added resources to nOps Scheduler, you can use the following features:

- Utilization Based Recommendation
- Workload Based Recommendation
- Storage Recommendation

The following request lists your **Utilization Based Recommendation**

`GET https://app.nops.io/svc/k8s_cost/scheduler_groups?page_number=1&page_size=20&sort_by=savings&sort_type=desc`
    ![](https://lh7-us.googleusercontent.com/088Ns1MB9qQRFzYXaDComfHSR_s_Jqrsg3hHzSsMVp0k8R-sBdw4GI-q2X0LPeKW8SGRC15o0n_W3uHD1A-6k8hEAhmw_KkGPMg4BcwK-iP3IOAr9EpZ0wZKxa-oaaZ1BD_pWFxfU5TrFjFNI0-uFbY)

The following request lists your **Workload Based Recommendation**

`GET https://app.nops.io/svc/k8s_cost/workload_scheduler_groups?page_number=1&page_size=20&sort_by=savings&sort_type=desc`
    ![](https://lh7-us.googleusercontent.com/dN9pAHd5gzem-3EBvwkhPkB1_eNLdeHij8PsimWjVQ16_cU9HaYrUHfCtVacSmefEBN6H0y6WjG-odOyMJXkZjpzcX1KWFTxJQ6wce7onjnhErlG7or-aEUh4awjMjtXTJpVWPhWLJEETsW25c9vOLc)

The following request lists your **Storage Recommendations**

`GET https://app.nops.io/svc/k8s_cost/nops_essentials?page_number=1&page_size=20&sort_by=savings&sort_type=desc`

![](https://lh7-us.googleusercontent.com/uCtrJuk8GyUjTZMxXYBmYbUllgMv07U_Gvd3JtzrTChQFPvMVwNMo4QCQktrA9gTG2OlhJmehCHhUep3LQXyE8JzGFT4AaTJKJK8-5CxdZaLph97M3OrjGgUptBqJICp-SUjt6pq4_OPiQn8FztHOdg)

### 4. (Optional) Create an EventBridge ###

An EventBridge is a notification that is triggered when a schedule is activated or deactivated. An EventBridge is created specific to an AWS account. Each AWS account must have an nOps Scheduler EventBridge configured. Any further schedules created in the account will use the same EventBridge. 

Before creating a new EventBridge, check if there is an EventBridge for the AWS account that is already configured. 

`GET https://app.nops.io/svc/notifications/eventbridge`

If the EventBridge integration does not exist, you should create a new EventBridge from the following steps:

In the **Create New EventBridge** page:

- Create a name for the EventBridge.
- Select the AWS account to deploy the EventBridge into. In the AWS accounts list, you will only see the accounts that you onboard into nOps.
- Select the region to deploy the EventBridge into.
- Click **Create**.

This [article](https://help.nops.io/solutions-using-eventbridge-with-nswitch-to-reduce-costs.html) provides more information on using EventBridge with nOps Scheduler. 

### 5. Creating a Schedule: ###

To create a schedule, use the following endpoint. 
```json

    POST https://app.nops.io/svc/notifications/scheduler/nops_scheduler
    Body: (Format: JSON)
    {"name":"test","project":<project_id>,"account_number":"<aws_account_id>","scheduled_by_tag_value":"38fdb370-32c9-11ee-92fc-0fc75763a04d","eventbridge_configuration":'<eventbridge id>',"hours_down":1,"resources":[],"actions":[{"action":"start","action_type":"selected_day_of_week","day":"mon","day_of_week":["mon"],"hour":0,"minute":0,"position":0},{"action":"stop","action_type":"selected_day_of_week","day":"sun","day_of_week":["sun"],"hour":23,"minute":0,"position":167,"action_details":{}}]}
```

![](https://lh7-us.googleusercontent.com/G9mElpY1yjqtOPlCTjQ0q8cWS3wss7-kCGtKQsCaey8NpdMRRiyoj2jCZgYNNX1KqCXUDJzmB4dSl2xv2o-CmwCpAdIqsfZLbxRchqB8tbe1SkYvg1EWh5rzlabOjkdtuFdDDGYvAR6PnSN2MgMcWxA)


{% include custom/series_related.html %}