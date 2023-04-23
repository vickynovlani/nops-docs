---
title: Evaluating the Cost Impact of a Changeset
keywords: savings, recommendations, solutions
tags: [savings, recommendations, solutions]
sidebar: mydoc_sidebar
permalink: solutions-evaluating-changeset-costs.html
folder: Solutions
---

It’s Friday 4 pm and you need to deploy a new Terraform configuration to AWS before you go home. You are required to verify that the new EC2 changes (create/update/delete) including RDS, do not go over budget. The last time you didn’t verify the changes and ended up costing the company $100,000 over the weekend because you accidentally deployed a fleet of high memory intense instances.

With nOps, this situation is now completely avoidable, you can now isolate the changes to the developer locally and see the cost changes before you deploy anything with a **simple Git pull request (Github Action)**. All you need to do is use the CLI/SDK in your DevOps workflow.

In this solution document we will explore:

1.  **nOps CLI and GitHub Actions (full automation)**
    
2.  **nOps SDK and CLI (custom automation)**
    
3.  **nOps SDK’s Pricing module and Cloud Infrastructure module (manual)**
    

You can use any of the above methods to investigate cost impacts for infrastructure changes made using Terraform to an AWS cloud account.

To learn more about the nOps SDK, see [nOps SDK Documentation](https://nopsteam.gitlab.io/nops-sdk/index.html).

# Value of Automated Cost-Impact Evaluation #
=========================================

## Lower Daily Costs ##
-----------------

Many small companies (and yes, even large enterprises) struggle to control costs while embracing cloud compute capacity. Costs are often focused on “keeping the engine running” and few resources are focused on managing capacity efficiently to lower daily costs of running a cloud infrastructure.

Optimize Resources and Budget Across the Organization
-----------------------------------------------------

You spin up resources, use them for a bit and leave them around just in case you need them. And then you forget about these resources and don’t touch them for six weeks. This situation is common but can disrupt your organizational budget. Well! With the help of nOps Pricing module, this will never happen again – the Pricing module will help you identify the cost impacts of resource changes so that you can manage them effectively up front.

Awareness of cost impacts enables early discussions with stakeholders to optimize resources and budgets across the organization, to understand reasons for cost increases and find tools to manage them.

Manage Capacity Costs for Sustainable Operations
------------------------------------------------

Managing capacity costs as business needs evolve is an investment in the future and ensures sustainable operations.

Cost-Effective Implementations
------------------------------

Strategies that consider the inter-connectivity and interdependency of costs to resources, lead to successful and cost-effective implementations.

Sometimes you migrate things you have no idea what it does and how useful it is, you migrate just in case one client might be using it. Find this technical debt and see what is happening… spin up when it is needed and nOps will tell you that it isn’t being used… you launch it one morning and shut it down the next morning.

Adjust Cloud Presence and Load-balance Across Regions
-----------------------------------------------------

With nOps you can pinpoint instances where utilization is extremely low within the specified time period. This will allow you to find candidate instances, which you can then switch to smaller sizes.

Check Cost Impact of Cloud-Server Configuration Change
------------------------------------------------------

With nOps **_Github Actions_** you can see the cost impact of any change that you make to your server configuration. You will see the cost impact in your local environment before the changes are pushed to the repository. The nOps Github Actions, will show you a table similar to the one below with the help of pre-commit hooks:


| **Project** | **Previous** | **New** | **Diff** |
| --- | --- | --- | --- |
| terraform_project1 | $167.04 | $83.38 | $83 |
| terraform_project3 | -   | $24.91 | $24.91 |
| terraform_project4 | $83.38 | $83.38 | $0.0 |
| terraform_project2 | $200.45 | -   | $200.45 |

Build Your Own Application on Top of the nOps SDK
-------------------------------------------------

Using the nOps open-source SDK you can build your own custom application on top of the SDK and integrate the cost impact check in your own CI/CD pipeline.

To learn more about how you can integrate the nOps CLI into your own CI/CD pipeline, see [nOps Precommit Client](https://github.com/nops-io/nops-precommit-client), which illustrates how nOps CLI was integrated into GitHub Actions.

Fully Automated Cost Retrieval with the nOps GitHub Actions
===========================================================

The nOps SDK is public, you can pull it down and integrate it in your own workflows. Anyone can build on top of our SDK, and this nOps CLI – which also is public and accessible to all – is the ultimate example.

What the nOps CLI does is that whenever you make terraform code changes and create a pull request, the CLI uses pre-commit hooks and GitHub Actions to get the estimated cost impact for your IAC projects impacted by the pull request code changes:

 ![](/tmpimg/cost-impact-changeset.png)

When you create a pull request, the GitHub Actions show the cost impact of the changeset in the form of a cost difference table:

 ![](/tmpimg/changeset-est-cost.png)

It wasn’t nOps who built the nOps CLI, it was built by the community, and it is the open-source community that maintains it.

Getting Started with nOps CLI and GitHub Actions
------------------------------------------------

**Prerequisites**

In addition to the [nOps SDK Prerequisites](https://docs.google.com/document/d/1-LfpAaTxfxj6J6V7LJpJDipJa4v60N-rAHj2WOTljSc/edit#heading=h.dxi8ibiclalj), you also need to ensure that you use a GitHub repository. A GitHub repository is essential since nOps uses GitHub Action to provide cost differences when you create a pull request for changes to Terraform IAC projects.

nOps CLI also requires Terraform installation to detect the Terraform changes and to build the required specs for nOps SDK, where the SDK will act on JSON specs.

**Installing the nOps CLI**

You can install and execute the nOps CLI independent of the nOps SDK – according to your requirements – in three different ways as a CLI, pre-commit hook, and GitHub Action. All you have to do is:

* Install the nOps CLI independently
    
* Install the nOps pre-commit hooks
    
* Use the nOps GitHub Action
    

To learn more about the independent installation and execution of the nOps CLI, see [nops-precommit-client](https://github.com/nops-io/nops-precommit-client) GitHub public repository.

**Install the nOps pre-commit Hooks**

You can Install the pre-commit hook using a simple pip command:

pip3 install pre-commit

Once the pre-commit hook is installed, use the nOps [.pre-commit-config.yaml](https://github.com/nops-io/nops-precommit-client/blob/main/.pre-commit-config.yaml) file **in your repo** to enable the nOps Pricing Hook and nOps Dependency Hook.

For more information on pre-commit see: [https://pre-commit.com/](https://pre-commit.com/). To learn more about the nOps pre-commit hooks, see [nops-precommit-client](https://github.com/nops-io/nops-precommit-client) GitHub public repository.

**Use the nOps GitHub Action**

GitHub Actions are workflows that are triggered when a specific event occurs in your repository. The nOps GitHub action provides cost differences, for changes made to Terraform IAC projects when you create a pull request. The action runs pricing checks for Terraform projects configured as a part of the [nOps-action.yml](https://github.com/nops-io/nops-precommit-client/blob/main/nOps-action.yml).

To learn how you can use the nOps GitHub action, see [nOps GitHub Action](https://github.com/nops-io/nops-precommit-client#nops-github-action).

**Account Module**

In addition to the Pricing module and Cloud Infrastructure module, the CLI also makes use of the nOps SDK Account module. This module exposes the Account class, which provides an entrypoint into interacting with the cloud accounts of your profile.

To learn more about the Account module, see [Account Module](https://nopsteam.gitlab.io/nops-sdk/nops_sdk.cloud_infrastructure.html).

Custom Automation of Cost Retrieval with the nOps CLI and SDK
=============================================================

The nOps CLI is open-source and publicly available. It was built on top of the nOps SDK to automate the retrieval of cost impact of change set with the help of pre-commit client and GitHub action for Terraform projects on GitHub.

You can use the open-source CLI and the nOps SDK to build your own custom automation for your preferred CI/CD pipeline.

To get a sneak peek of how you can create your own custom automation, see [nOps Precommit Client](https://github.com/nops-io/nops-precommit-client) to get a sense of how the community was able to achieve full automation.

To implement the full automation, the community used these SDK modules:

\# To estimate cost impact of a IaC changeset and display pricing using nOps SDK.

from nops_sdk.pricing import CloudCost

from nops\_sdk.cloud\_infrastructure.enums import AWSRegion

from nops\_sdk.cloud\_infrastructure.cloud_operation import Periodicity

\# An entrypoint into interacting with the cloud accounts of your nOps profile to get the cloud resource dependencies

from nops_sdk.account.account import Account

\# The main entry point to the nOps SDK to manage nOps accounts.

from nops_sdk.api import APIClient

To learn more about these SDK modules, their purpose, and functionality, see [nOps SDK](https://nopsteam.gitlab.io/nops-sdk/nops_sdk.api.html).

The community also created these CLI utilities, constants, subcommands, enum inputs, and libraries to achieve the full automation for cost retrieval:

from nops\_cli.utils.logger\_util import logger

\# The generic alias for Terraform resource name.

from nops\_cli.constants.resource\_mapping import TERRAFORM\_RESOURCE\_MAPPING

\# Interact with nOps CLI.

from nops\_cli.utils.execute\_command import execute

\# Get the terraform outputs/states for nops pricing API's.

from nops\_cli.subcommands.dependancy.terraform\_dependency import

from nops\_cli.subcommands.pricing.terraform\_pricing import TerraformPricingTerraformDependency

\# nOps pricing dependencies

from nops\_cli.constants.input\_enums import Periodicity, IacTypes

\# Get the terraform outputs/states for nops dependency API's.

from nops_cli.libs.terraform import Terraform

from nops\_cli.libs.get\_accounts import NOpsAPIClient

To learn more about these utilities, constants, subcommands, enum inputs, and libraries, see this [nOps precommit client](https://github.com/nops-io/nops-precommit-client) GitHub repository.

Manual Retrieval of Cost Impact with the nOps SDK
=================================================

The nOps SDK consists of several modules, but this Solution Doc — evaluating the cost impact of a Terraform changeset — focuses on the Pricing module and the Cloud Infrastructure module.

 ![](/tmpimg/changeset-cost-manual.png)

These two modules collectively form the basis of evaluating the cost impact of a changeset. Here is an example Python code snippet that show how these two modules work together to get the cost changes:

```python
>>> from nops_sdk.pricing import CloudCost

>>> from nops_sdk.cloud_infrastructure.enums import AWSRegion

>>> from nops_sdk.cloud_infrastructure.cloud_operation import Periodicity

>>> spec = [

        {

            "new_data": {"instance_type": "t2.micro"},

            "old_data": None,

            "operation_type": "create",

            "resource_type": "ec2",

            "ami": "ami-0269f532"

        },

        {

            "new_data": {"instance_type": "t2.nano", "ami": "ami-00bb6f60"},

            "old_data": {"instance_type": "t2.micro", "ami": "ami-0269f532"},

            "operation_type": "update",

            "resource_type": "ec2"

        },

        {

            "new_data": None,

            "old_data": {

                "instance_class": "db.t2.micro",

                "engine": "oracle-ee",

                "license_model": "bring-your-own-license",

                "multi_az": True

            },

            "operation_type": "delete",

            "resource_type": "rds",

        },

    ]

>>> cloud_cost = CloudCost(aws_region=AWSRegion('us-west-2'), spec=spec)

>>> cloud_cost.load_prices()

****After you load the prices, you can compute and output prices for any supported `Periodicity` at no significant cost.****

>>> cloud_cost.compute_cost_effects(period=Periodicity('monthly'))

>>> cloud_cost.output_report()

Create t2.micro EC2 instance with a monthly cost impact of 8.35

Delete db.t2.micro RDS instance with a monthly cost impact of -9.79

Update t2.micro EC2 instance to t2.nano EC2 instance with a monthly cost impact of -4.18 

```

The example above is how you can access the nOps SDK programmatically.

Pricing Module
--------------

The nOps Pricing module provides estimated costs for Terraform Infrastructure as Code (IaC) projects using GitHub pull requests.

The pricing module exposes the nops_sdk.pricing.CloudCost class, which is then used to estimate cost impact of a IaC changeset.

To learn more about the Pricing module, see [Pricing Module](https://nopsteam.gitlab.io/nops-sdk/nops_sdk.pricing.html).

Cloud Infrastructure
--------------------

This module provides Enum and Cloud Operation classes which form the backbone of nOps SDK’s cloud pricing and dependency functionality.

To learn more about the Cloud Infrastructure module, see [Cloud Infrastructure Module](https://nopsteam.gitlab.io/nops-sdk/nops_sdk.cloud_infrastructure.html).

nOps SDK Further Capabilities
-----------------------------

The AWS product families that nOps Pricing module supports are:

* EC2= ‘ec2’
    
* RDS= 'rds'
    
* EKS= 'aws\_eks\_cluster'
    
* EKS\_NODE\_GROUP= 'aws\_eks\_node_group'
    
* propertyresource_class: Resource
    

**EC2**

This snippet is an example of the EC2 specs in Python for calling the nOps SDK:

```python

{

     "new_data": {"instance_type": "t2.micro"},

     "old_data": None,

     "operation_type": "create",

     "resource_type": "ec2",

     "ami": "ami-0269f532"

}

```

**RDS**

This snippet is an example of the RDS specs in Python for calling the nOps SDK:

```python
{

     "new_data": None,

     "old_data": {

         "instance_class": "db.t2.micro",

         "engine": "oracle-ee",

         "license_model": "bring-your-own-license",

         "multi_az": True

     },

     "operation_type": "delete",

     "resource_type": "rds",

}
```

**EKS Cluster**

This snippet is an example of the EKS Cluster specs in Python for calling the nOps SDK:

```python

{

     'id': None,

     'resource_type': 'aws_eks_cluster',

     'operation_type': 'create',

     'old_data': None,

     'new_data': {

        'name': 'devopsthehardway-cluster',

     }

}

```

**EKS Node Group**

This snippet is an example of the EKS Node Group specs in Python for calling the nOps SDK:

```python
{

     'id': None,

     'resource_type': 'aws_eks_node_group',

     'operation_type': 'create',

     'old_data': None,

     'new_data': {

         'cluster_name': 'devopsthehardway-cluster',

         'instance_types': ['t3.xlarge'],

         'node_group_name': 'devopsthehardway-workernodes',

         'scaling_config': [

             {

             'desired_size': 1,

             'max_size': 1,

             'min_size': 1

             }

         ],

     }

}

```

To access the nOps programmatically via the nOps SDK, all you need to do is [Install nOps SDK](https://docs.google.com/document/d/1-LfpAaTxfxj6J6V7LJpJDipJa4v60N-rAHj2WOTljSc/edit#heading=h.la95x0cpj6sp).

To learn more about the nOps SDK and how you can use it, see [nOps SDK](https://docs.google.com/document/d/1-LfpAaTxfxj6J6V7LJpJDipJa4v60N-rAHj2WOTljSc/edit#heading=h.k7ckowsv43dq) and [nOps SDK Documentation](https://nopsteam.gitlab.io/nops-sdk/index.html).

Getting Started with nOps SDK
-----------------------------

**Prerequisites**

Before you can use the nOps SDK for evaluating the cost impact of a changeset, you must configure your AWS cloud accounts to allow nOps to pull metadata from the accounts during your setup.

You can do this by using one of the following methods:

* CloudFormation ([Adding an AWS account to nOps with Automatic Setup](onboarding-aws-with-automatic-setup.html))
    
* Manually setting up IAM Roles, Policies, and S3 Buckets ([Adding an AWS account to nOps with Manual Setup](onboarding-aws-with-manual-setup.html))
    

For more information about cloud account configuration, see [Getting Started](tag_getting_started.html).

The nOps SDK’s Pricing module displays costs for projected resource changes when you use a Terraform project to implement them (It predicts cost changes for Terraform changes).

In this section of the solution doc, we will walk you through how you can install and begin using the nOps SDK today. All you have to do is:

* Installing the nOps SDK
    
* Configure the nOps API Key
    

Refer to the [nOps SDK Documentation](https://nopsteam.gitlab.io/nops-sdk/index.html) to learn about this process in depth.

**Requirements**

Before you continue, make sure you have:

* Python 3.9 or newer
    
* requests
    
* boto3
    
* nOps API Key
    

To learn more about how to get the nOps API key, see [Create an API key](https://nopsteam.gitlab.io/nops-sdk/installation.html#create-an-api-key).

**Installing the nOps SDK**

The nOps SDK and nOps CLI are available in the form of a Python library that you can install from TestPyPI with a simple pip command:

pip install --index-url [https://test.pypi.org/simple/](https://test.pypi.org/simple/) nops-sdk --extra-index-url [https://pypi.org/simple](https://pypi.org/simple)

Follow the instructions in the [nOps SDK documentation](https://nopsteam.gitlab.io/nops-sdk/installation.html#install-the-nops-sdk-library-from-testpypi) to learn about the installation procedure.

* * *

**Note:** Currently nOps SDK only displays costs for resource changes you make, or plan to make to EC2, EKS, and RDS resources types for AWS Cloud accounts.