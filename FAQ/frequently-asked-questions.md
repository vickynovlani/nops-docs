---
title: Frequently Asked Questions
layout: default
nav_order: 4
has_children: false
---

# Frequently Asked Questions #

## Does nOps Require any Write Policy? ##

nOps requires the following write permissions for setup (optional):

*   logs:CreateLogGroup, logs:CreateLogStream, logs:PutLogEvents — These permissions provide the ability to create automatic setup on nOps.
    
*   s3:\* (billing bucket only) — or reuse the existing one for CUR setup.
    
*   s3:CreateBucket — This permission provides nOps the ability to create a new bucket for CUR setup. Our Cloudformation creates and removes the policy as part of automated set-up in order to generate an S3 bucket if it does not exist.
    

nOps requires the following write policies for operation:

*   cur:PutReportDefinition — This permission helps the automatic account setup process. It will create a new Cost and Usage Report if it doesn’t exist and provides a smooth cost integration with nOps. Clients can deny this permission and can do the setup manually.
    
*   wellarchitected — nOps needs this permission to interact with this service, and generate reports. If the client disables this permission, the Workload features and WAFR report might not work correctly.
    


## How does nOps Deploy to the Customer Environment? ## 


The nOps data platform uses three strategies to ingest data from our customer environments: pulling data from AWS and Azure data sources, forwarding events in NRT from AWS, and forwarding high resolution metrics from both managed and standalone Kubernetes clusters. Here’s how we deploy into customer’s in an easy automated fashion:

*   IAM roles which can be applied through our [Cloudformation automation](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/quickcreate?templateURL=https://s3-us-west-2.amazonaws.com/nops-users/nOpsRole.yaml&stackName=Nops-Integration-1fc5&param_NopsAuthURL=https%3A//app.nops.io/c/aws/integration/%3Factive_token%3D1fc52ac0096c20439908a6606a989d9595d7&param_SystemBucketID=adf&param_ExternalID=0eacb750-0f94-11ed-9eee-8169c6f45fe1&param_ActiveToken=1fc5) or using our [account-registration IaaC project](https://github.com/nops-io/nops-cloud-account-registration) allow our backend processes to pull multiple data sources, including reading progressive log files from S3 buckets (Cost and Usage, VPC Flow logs), resource metadata, and cloud trail events.
    
*   The [nops-aws-forwarder](https://github.com/nops-io/nops-aws-forwarder) is a Lambda function that forwards events for real-time automation. This allows us to drive mission critical optimization workflows like Reserved Instance automation and keeping our Graph Data API refreshed. The Lambda forwarder can also be launched in minutes using our Cloudformation template.
    

The [nOps Kubernetes agent](https://github.com/nops-io/nops-k8s-agent) is a lightweight client that allows us to ingest high-resolution metrics from Kubernetes clusters for optimization and detailed shared resource cost allocation. It can be deployed into any type of Kubernetes environment, including EKS. The agent is deployed via IaaC using helm charts and creates a pod in the customers cluster to forward metrics to our data platform.