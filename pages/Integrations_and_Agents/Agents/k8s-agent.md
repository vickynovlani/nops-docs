---
title: Kubernetes Agent
keywords: reporting, integrations
tags: [agents_integrations]
sidebar: mydoc_sidebar
permalink: k8s-agent.html
folder: Integrations_and_Agents
---

The nOps Kubernetes (K8s) agent will run in the K8S environment to collect metrics and send them to nOps.

1. TOC
{:toc}


## Install nOps K8s Agent


nOps K8s Agent shares the details of all the pods and containers in your K8s to nOps for cost optimization recommendations.

This worker contains a database to keep user entries, pulls metadata from their accounts on a scheduled basis, and publishes the output to kafka topic.

In this document you will learn how to deploy the nOps K8s agent via Helm Chart. nOps uses Prometheus, a monitoring app, where you write YAML files, nOps then bundle them in Helm creating a Helm Chart for monitoring K8s via the nOps K8s agent.

Before you get started with the installation of nOps K8s agent, make sure you set the Kubernetes context in which you want to deploy the agent (prod, dev, etc).

Requirements
============

The installation requirements of nOps K8s Agent are divided into “Development” and “Development and Deployment”.

For only _Development_, the requirements are:

* [Tilt](https://tilt.dev/)
    
* make
    

For _Development and Deployment_, the requirements are:

* [Tilt](https://tilt.dev/)
    
* Make
    
* [Helm](https://helm.sh/)
    
* Kubernetes command line tool, kubectl, connected to any K8s cluster i.e., [k3d](https://k3d.io/v5.1.0/).
    

Development
===========

For simple _Development_ of the nOps K8s Agent, copy the content of the `./charts/nops-k8s-agent-dev/values.yaml` file to `./charts/nops-k8s-agent-dev/local_values.yaml` file and enter your configuration details to `local_values.yaml` file.

You can use any K8s cluster provider, this example uses k3d:

\# Launch cluster  
make dev_infra  
  
\# Launch stack  
make run

Development and Deployment
==========================

The _Development and Deployment_ is divided into four 5 steps:

1.  Get the repository
    
2.  Create a namespace
    
3.  Deploy Prometheus
    
4.  Configure values.yaml
    
5.  Deploy Agent from Source Code or Deploy Agent via Helm Repo
    

Get the repository
------------------

To install the K8s agent, the first step is to get the latest release version of the agent. As the current release version uses a helm chart for deployment, to get the chart files, you need to clone the [nOps K8s Agent](https://github.com/nops-io/nops-k8s-agent) public GitHub repository.

nOps also has a [zip file and tar.gz](https://github.com/nops-io/nops-k8s-agent/releases) file for every release in the repository.

Create namespace
----------------

The second step is to create a namespace for the nOps K8s agent using **kubectl**. Use these commands to create the namespace:

kubectl create namespace nops-k8s-agent  
kubectl config set-context --current --namespace=nops-k8s-agent

Deploy Prometheus
-----------------

The third step is to use Prometheus to deploy and launch your nops-k8s-agent namespace. Use these commands deploy and launch your nops-k8s-agent namespace:

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts  
helm install prometheus prometheus-community/kube-prometheus-stack

You can also use your own Prometheus instance to launch the nops-k8s-agent namespace. If you don’t have Prometheus already installed, you will need to install it first.

Configure values.yaml
---------------------

The `values.yaml` file (`./charts/nops-k8s-agent/values.yaml`) is a part of the Helm templating engine. It uses the configuration in the `values.yaml` file for the templates to create the K8s agent Helm Chart.

These are the variables required to create the K8s agent Helm Chart:

* `APP_PROMETHEUS_SERVER_ENDPOINT` — Depends on your Prometheus stack installation (different for every person and every cluster).
    
* `APP_NOPS_K8S_AGENT_CLUSTER_ID` — Needs to match your cluster ID.
    
* `APP_NOPS_K8S_COLLECTOR_API_KEY` — See, [nOps Developer API](developer-getting-started.html) to learn how to get your API key.
    
* `APP_NOPS_K8S_COLLECTOR_AWS_ACCOUNT_NUMBER` \- The 12-digit unique account number of the AWS account, which is configured within nOps.
    

These above values if changed in the directory will become the new default. You can override these values during deployment of the agent via helm repo.

You can either use your own Chart values file, or you can modify and use our example `setup_values` script to fetch `variable_env` from Parameter Store SSM (Not encrypted):

\# Patch values for env_variables using the SSM store.  
python3 deploy/setup\_values.py $CI\_ENVIRONMENT_SLUG charts/nops-k8s-agent/values.yaml > /tmp/values.yaml

Deploy Agent From Source Code
-----------------------------

Prior knowledge of K8s Helm is necessary to understand the commands and deploy the agent from source code. If you are not comfortable with using deploying from source code, you can deploy the agent via helm repo.

Following is the Helm command that will start the Helm Chart and deploy the K8s agent on the Kubernetes cluster:

```
\# Upgrade chart.  
helm \  
  upgrade -i nops-k8s-agent ./charts/nops-k8s-agent \  
  -f /tmp/values.yaml \  
  --namespace nops-k8s-agent \  
  --set image.repository=ghcr.io/nops-io/nops-k8s-agent \  
  --set image.tag=deploy \  
  --set env\_variables.APP\_ENV=live \  
  --wait --timeout=300s
```

If instead of fetching the value from the Parameter Store SSM you decided to change add the value in code, then omit the `-f /tmp/values.yaml \` from the command.

Deploy Agent via Helm Repo
--------------------------

Before you deploy your agent via Helm repo, make sure your values.yaml file is correctly configured. See, Configure values.yaml to learn more.

Use these commands to deploy the agent via Helm repo:

helm repo add nops-k8s-agent https://nops-io.github.io/nops-k8s-agent  
helm install -f values.yaml nops-k8s-agent

To deploy the K8s agent on multiple AWS accounts associated with nOps you can give additional values in the above command to replace the defaults you have set in the values.yaml file.

Release Management
==================

Helm 2 client (CLI) and the Server (Tiller) — Creates the services and keeps track of release versions.

Helm 3 client (CLI) Server (Binary) — Release management feature is more challenging due to security issues.

Releases are available in the nOps [nOps K8s Agent](https://github.com/nops-io/nops-k8s-agent) public repository.

Some helpful Helm commands to manage release versions:

helm install &lt;chartname&gt;  
helm upgrade &lt;chartname&gt; // for changes to existing deployment instead of creating a new one.  
helm rollback &lt;chartname&gt; // if anything goes south.