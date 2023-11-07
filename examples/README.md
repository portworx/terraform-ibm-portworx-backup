# Getting Started

This guide is intended to provide a quick start to users who want to install PX-Backup for Kubernetes on their existing IKS Clusters using Terraform.

## Pre-requisites

- Terraform >= 0.13
- Already Provisioned IKS Cluster
- `ibmcloud ks` cli plugin is not needed by the Terraform script but is needed to get the kubeconfig. e.g. `ibmcloud ks cluster config --admin --cluster <cluster_name | cluster_id>`
- `kubectl` installed and pointed to the correct IKS Cluster

## Available examples

There is 1 example included:

- Install PX-Backup for Kubernetes on existing IKS cluster using IBM catalog **[px-backup-ibm-catalog-install](https://github.com/atrivedi-px/terraform-ibm-portworx-backup/tree/ibm-catalog-px-backup-install/examples/px-backup-ibm-catalog-install)**