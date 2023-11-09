# Getting Started

This guide is intended to provide a quick start to users who want to install PX-Backup for Kubernetes on their existing IKS Clusters.

## Pre-requisites

- Terraform >= 0.13
- Already Provisioned IKS Cluster
- `ibmcloud ks` cli plugin is not needed by the Terraform script but is needed to get the kubeconfig. e.g. `ibmcloud ks cluster config --admin --cluster <cluster_name | cluster_id>`
- `kubectl` installed and pointed to the correct IKS Cluster

## Setting Up Environment

In this example we'll specifically walk you through the process of installing PX-Backup for Kubernetes on IKS using IBM Cloud Catalog.

> Clone this Repo and `cd` into the `examples/px-backup-ibm-catalog-install`, and now you can issue the following commands to proceed.

### Required Data/Values

These are following data/values required that shall be passed to the terraform module as variables.

- IKS Cluster name
- IBM Cloud API Key
- The Resource Group name where the Cluster exists, **the Portworx Enterprise Service Instance will be created in the same Resource Group.**

### Creating Variables

Before you run the `terraform` scripts, you can use `terraform.tfvars` or `Environment Variables` or `-var` or `-var-file` in supplement with the examples. Refer to [Terraform Documentation](https://www.terraform.io/language/values/variables#assigning-values-to-root-module-variables)

We shall use `terraform.tfvars` in these examples.

> Example `terraform.tfvars` **(You can find a `terraform.tfvars.sample` file in each example directory, rename the file and set the correct values)**

```terraform
cluster_name = "your-iks-cluster-name"
ibmcloud_api_key = "ibm-cloud-api-key"
resource_group = "your-resource-group-name"
```

Create the above file with name `terraform.tfvars`
Check the `examples/px-backup-ibm-catalog-install/variables.tf` to understand what are the variables required

## Setting up Credentials

```sh
export IBMCLOUD_API_KEY="secret_ibm_cloud_key"
ibmcloud login
ibmcloud ks cluster config --admin --cluster <cluster_name | cluster_id>
```

## Installation

```sh
terraform init
terraform plan -out tf.plan
terraform apply tf.plan
terraform output
```
