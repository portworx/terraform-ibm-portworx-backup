# Terraform Module for PX-Backup for Kubernetes on IBM Cloud

IBM Cloud provides an option to provision PX-Backup for Kubernetes on IKS cluster through IBM Catalog. This repo hosts the terraform module which can be used in conjunction with existing terraform scripts to provision PX-Backup for Kubernetes on IKS.

## Usage

Include the below module definition in a `.tf` file to deploy Portworx Enterprise with the default values.

> Please take a look at the default values in the **Input Variables** section to understand the default behavior of this module.

```terraform
module "portworx_backup" {
  source                    = "portworx/portworx-backup/ibm"
  cluster_name              = "my-iks-cluster"
  resource_group            = "my-resource-group"
  ibmcloud_api_key          = "my-api-key"
}
```

## Features

This terraform module provides the following features for seamless adoption:

- Declarative Installation/Uninstallation
- Easy Integration with existing Terraform Scripts
- Built-in Post Installation Validation

## Getting Started

> Please refer to the [Getting Started Guide](https://github.com/atrivedi-px/terraform-ibm-portworx-backup/blob/ibm-catalog-px-backup-install/examples/README.md) to install PX-Backup for Kubernetes on an IKS using IBM Catalog.
> This guide outlines the steps to set up an environment and deploy on IBM Cloud.

## Examples

The below hyperlinks guide you to understand and demonstrate the features and capabilities of this Terraform module:


## Requirements

The following are requirements needed to be installed on the host machine where the terraform commands will be issued.
`terraform`, `kubectl` and `ibmcloud` libraries are needed as some bash scripts are required for validation checks.

Refer to the table below for more details:

| Name      | Version          |
| --------- | ---------------- |
| terraform | 0.13 and above   |
| kubectl   | 1.22.0 and above |
| ibmcloud  | 2.10.0 and above |

## Providers

Following providers are used by our modules, to manage resources on IBM Cloud:

| Name             | Version           |
| ---------------- | ----------------- |
| ibm-cloud/ibm    | 1.48.0 and above |
| hashicorp/random | 3.4.3 and above   |
| hashicorp/null   | 3.1.1 and above   |

## Resources

Below **resources** and **data sources** are created to manage the resources of terraform module:

| Name                                                                                                                                                   | Type        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------- |
| [ibm_resource_instance.portworx_backup](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/resource_instance)                        | resource    |
| [null_resource.validate_portworx_backup_installation](https://registry.terraform.io/providers/hashicorp/null/latest/docs/resources/resource)                                | resource    |
| [random_uuid.unique_id](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/uuid)                                           | resource    |
| [ibm_resource_group.resource_group](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/data-sources/resource_group)                              | data source |

## Input Variables

Below list of input variables can be provided to the Terraform module. There are some default values already set for this module which can be overridden otherwise. Please read through the description and default values before handling advanced scenarios of using this module.

| Name                                                                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Type                                                                                                                                                                     | Default                                                                                                                                                                                     | Required |
| ------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------: |
| <a name="input_cluster_name"></a> [cluster_name](#input_cluster_name)                            | Name of existing IKS cluster                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | `string`                                                                                                                                                                 | n/a                                                                                                                                                                                         |   yes    
| <a name="input_ibmcloud_api_key"></a> [ibmcloud_api_key](#input_ibmcloud_api_key)                | Get the ibmcloud api key from https://cloud.ibm.com/iam/apikeys                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | `string`                                                                                                                                                                 | n/a                                                                                                                                                                                         |   yes 
| <a name="input_portworx_service_name"></a> [portworx_service_name](#input_portworx_service_name) | Name to be provided to the PX-Backup for Kubernetes service to be deployed                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | `string`                                                                                                                                                                 | `"px-backup"`                                                                                                                                                                     |    no    |
| <a name="input_pwx_plan"></a> [pwx_backup_plan](#input_pwx_plan)                                        | Portworx plan type                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | `string`                                                                                                                                                                 | `"px-backup-enterprise"`                                                                                                                                                                           |    no    |
| <a name="input_region"></a> [region](#input_region)                                              | The region PX-Backup for Kubernetes will be installed in: us-south, us-east, eu-gb, eu-de, jp-tok, au-syd, etc.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | `string`                                                                                                                                                                 | `"us-east"`                                                                                                                                                                                 |    no    |
| <a name="input_resource_group"></a> [resource_group](#input_resource_group)                      | Resource group of existing IKS Cluster                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | `string`                                                                                                                                                                 | n/a                                                                                                                                                                                         |   yes    |
| <a name="input_tags"></a> [tags](#input_tags)                                                    | Optional Tags to be added, if required.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | `list(string)`                                                                                                                                                           | `[]`                                                                                                                                                                                        |    no    |
| <a name="input_namespace"></a> [namespace](#input_namespace)                                     | Namespace to deploy PX-Backup for Kubernetes in the IKS                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | `string`                                                                                                                                                                 | `"px-backup-namespace"`                                                                                                                                                                             |    no    |


## Output Variables

Table below lists out the output variables to be read or referred after successful application/execution of the Terraform module.

| Name                                                                                                                                | Description                                                         |
| ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| <a name="output_portworx_backup_installation_details"></a> [portworx_backup_name](#output_portworx_backup_installation_details)                      | Name of the service deployed   |
| <a name="output_portworx_backup_installation_details"></a> [portworx_backup_state](#output_portworx_backup_installation_details)                      | State of the service deployed   |

## License

Apache License 2.0 - Copyright 2023 Pure Storage, Inc.