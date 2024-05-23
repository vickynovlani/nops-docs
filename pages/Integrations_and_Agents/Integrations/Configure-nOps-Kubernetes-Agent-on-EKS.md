---
title: Configure nOps Kubernetes Agent on EKS
keywords: CostContainer, integrations
tags: [agents_integrations]
sidebar: mydoc_sidebar
permalink: Configure-nOps-Kubernetes-Agent-on-EKS.html
folder: Integrations_and_Agents
series: [agents_integrations]
weight: 6.0
---

{: .no_toc }

### This document serves as a comprehensive guide, walking you through the setup and deployment procedures, guaranteeing seamless integration with the nOps platform to enhance operational efficiency.The nOps Kubernetes Agent (nops-k8s-agent) plays a vital role in streamlining cloud infrastructure management.Its purpose is to:

1) Gather metadata from Kubernetes clusters.

2) Safely transmit this information to an Amazon S3 bucket.This functionality empowers the nOps platform to:1) Analyze the accumulated data.
3) Offer actionable insights for optimizing costs and managing resources.

## Prerequisites

1) You must have an active nOps account. If you do not have one, please register on the nOps website.2. Make sure you have access to a Kubernetes cluster (recommended version v1.23.6 or later) to deploy the agent.



## Steps to Configure nOps Kubernetes Agent

1. Go to Organization setting > Integrations > Container cost Tab
2. Select the AWS account you want to set up k8s cost agent.
3. Click on Setup button.
4. You will be redirected to the AWS console > cloud formation stack page. (make sure you are already logged into AWS account in the same browser tab).

![](https://lh7-us.googleusercontent.com/nPx5BeHTlSh28DP045-42-OmhPy15SPDHv5brOSvld3Z_VZbIzcg4OZJqpXBXoFrx2f2yujyc9zXoj48kDFMMmz4TcsWY8TNLFmaUdxq-prZF_P4hZmVKeArUs8CtWraHYSAEuA2zoEmj9ryZVhz1Eo)

5. Create a stack.
6. Return to nOps platform and check the status. 

![](https://lh7-us.googleusercontent.com/UaddssjZ6rK9aZEa3luYO_SHQEqxorkhyBEwudJoL-riDinH6EGe-FseGYg4Dtdh5QX4m9xZfAg0T1YyT7_DZWE8Bo60-AqctR6dCuh-brL58PRCXqRtlneK1Q-41nBpVDBU7vP-OPSZXHJ6092RkVM)

7. As soon as the status is showing “configured” click on Generate script button.

8. Copy the script to any application like , notepad. 
9. On AWS cloud formation page , go to output and copy user name.
10. Redirect to the IAM users page and find your user name.
11. follow the steps to create access key. 
12. Copy Access ID and Key and paste it into generated script.
13. Again , Go back to AWS console and open your eks cluster to copy the cluster ARN and paste it in the same generated script and save the file.
14. Change the permissions of the file and make it an executable one. 

To change the permission of that, 
you run:Chmod +x script\_name.sh
And to execute:./script\_name.sh

15. Run the Generated script file into terminal to configure the agent as shown below.

![](https://lh7-us.googleusercontent.com/Ov4lnnsBQvECBDeQXWMK1Jok732HbyQadFYPp6scm8nyZWeR-PQ6WFVQGa0RVMy94ux4hgtwIlQbJ7IopjVp6MTcWr96xBpnZQNVrzrippPJfUU2C-uiQAhpGok5f0IOfqwpiYqf-Vd1lEsPeWBZYJs)


After successfully configuration, you gain complete visibility into your workloads, tailored to your preferred level of detail. While your EKS expenditure typically remains opaque, pinpointing cloud inefficiencies can be a challenge. nOps streamlines this process by automatically detecting wastage through CPU and memory metrics, empowering you to optimize resources and realize immediate cost savings.

**FAQs**

1. I have prometheus installed and I use it for a variety of purposes in my cluster, will this affect that?
 **Ans:** No, our agent leverages it's own prometheus in it's own namespace so that doesn't affect your current deployments.

