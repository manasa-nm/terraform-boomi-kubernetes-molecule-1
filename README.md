<!-- BEGIN_TF_DOCS -->
# Terraform Module Project

:no\_entry\_sign: Do not edit this readme.md file. To learn how to change this content and work with this repository, refer to CONTRIBUTING.md

## Readme Content

This file will contain any instructional information about this module.

## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.0.7 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | ~> 5.31.0 |
| <a name="requirement_helm"></a> [helm](#requirement\_helm) | ~> 2.12.1 |
| <a name="requirement_kubernetes"></a> [kubernetes](#requirement\_kubernetes) | ~> 2.24.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | ~> 5.31.0 |
| <a name="provider_helm"></a> [helm](#provider\_helm) | ~> 2.12.1 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_asg"></a> [asg](#module\_asg) | terraform-aws-modules/autoscaling/aws | ~>7.3.1 |
| <a name="module_bastion-sg"></a> [bastion-sg](#module\_bastion-sg) | terraform-aws-modules/security-group/aws | ~> 5.1.0 |
| <a name="module_efs"></a> [efs](#module\_efs) | terraform-aws-modules/efs/aws | ~> 1.0 |
| <a name="module_eks"></a> [eks](#module\_eks) | terraform-aws-modules/eks/aws | ~> 19.12 |
| <a name="module_eks_blueprints_addons"></a> [eks\_blueprints\_addons](#module\_eks\_blueprints\_addons) | aws-ia/eks-blueprints-addons/aws | ~> 1.0 |
| <a name="module_lambda_function"></a> [lambda\_function](#module\_lambda\_function) | terraform-aws-modules/lambda/aws | 6.5.0 |
| <a name="module_vpc"></a> [vpc](#module\_vpc) | terraform-aws-modules/vpc/aws | ~> 5.4.0 |

## Resources

| Name | Type |
|------|------|
| [aws_iam_policy.BastionHostPolicy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_policy) | resource |
| [aws_kms_key.lambda_kms_key](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/kms_key) | resource |
| [helm_release.boomi_molecule](https://registry.terraform.io/providers/hashicorp/helm/latest/docs/resources/release) | resource |
| [aws_eks_cluster_auth.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/eks_cluster_auth) | data source |
| [aws_lambda_invocation.boomi-license-validation](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/lambda_invocation) | data source |
| [aws_subnet.aws_private_subnet_cidr](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/subnet) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_aws_profile"></a> [aws\_profile](#input\_aws\_profile) | AWS profile for the deployment. | `string` | n/a | yes |
| <a name="input_bastion_key_name"></a> [bastion\_key\_name](#input\_bastion\_key\_name) | EC2 Keypair Name for Bastion Host | `string` | n/a | yes |
| <a name="input_bastion_security_group_id"></a> [bastion\_security\_group\_id](#input\_bastion\_security\_group\_id) | Security Group ID of bastion host. This will be added to EKS for access from Bastion Host. | `string` | n/a | yes |
| <a name="input_boomi_account_id"></a> [boomi\_account\_id](#input\_boomi\_account\_id) | Boomi Account ID | `string` | n/a | yes |
| <a name="input_boomi_install_token"></a> [boomi\_install\_token](#input\_boomi\_install\_token) | Boomi AtomSphere API Tokens | `string` | n/a | yes |
| <a name="input_boomi_password"></a> [boomi\_password](#input\_boomi\_password) | Boomi Password, this is not needed when boomi\_install\_token is provided. | `string` | n/a | yes |
| <a name="input_boomi_username"></a> [boomi\_username](#input\_boomi\_username) | Boomi Username | `string` | n/a | yes |
| <a name="input_existing_private_subnets_ids"></a> [existing\_private\_subnets\_ids](#input\_existing\_private\_subnets\_ids) | List of private subnet ids | `list` | n/a | yes |
| <a name="input_existing_public_subnets_ids"></a> [existing\_public\_subnets\_ids](#input\_existing\_public\_subnets\_ids) | List of public subnet ids | `list` | n/a | yes |
| <a name="input_existing_vpc_id"></a> [existing\_vpc\_id](#input\_existing\_vpc\_id) | VPC ID for existing VPC | `string` | n/a | yes |
| <a name="input_availability_zones"></a> [availability\_zones](#input\_availability\_zones) | A list of availability zones names | `list` | <pre>[<br>  "us-west-2a",<br>  "us-west-2b",<br>  "us-west-2c",<br>  "us-west-2d"<br>]</pre> | no |
| <a name="input_bastion_ami_id"></a> [bastion\_ami\_id](#input\_bastion\_ami\_id) | AMI ID for Bastion Host | `string` | `"ami-07dfed28fcf95241c"` | no |
| <a name="input_bastion_remote_access_cidr"></a> [bastion\_remote\_access\_cidr](#input\_bastion\_remote\_access\_cidr) | CIDR Range for bastion Host | `string` | `"0.0.0.0/0"` | no |
| <a name="input_boomi_script_location"></a> [boomi\_script\_location](#input\_boomi\_script\_location) | n/a | `string` | `""` | no |
| <a name="input_cluster_endpoint_public_access_cidrs"></a> [cluster\_endpoint\_public\_access\_cidrs](#input\_cluster\_endpoint\_public\_access\_cidrs) | CIDR Range for EKS public access | `string` | `"0.0.0.0/0"` | no |
| <a name="input_cluster_version"></a> [cluster\_version](#input\_cluster\_version) | EKS Cluster Version | `string` | `"1.26"` | no |
| <a name="input_create_new_vpc"></a> [create\_new\_vpc](#input\_create\_new\_vpc) | If set to true, will create new VPC. If set to false, the existing provided vpc is used | `bool` | `false` | no |
| <a name="input_deployment_name"></a> [deployment\_name](#input\_deployment\_name) | Deployment Name for the boomi terraform deployment. | `string` | `"boomi-eks-blueprint"` | no |
| <a name="input_kubectl_version"></a> [kubectl\_version](#input\_kubectl\_version) | n/a | `map` | <pre>{<br>  "1.25": "1.25.9/2023-05-11",<br>  "1.26": "1.26.4/2023-05-11",<br>  "1.27": "1.27.1/2023-04-19"<br>}</pre> | no |
| <a name="input_private_subnets"></a> [private\_subnets](#input\_private\_subnets) | A list of private subnets CIDR range | `list` | <pre>[<br>  "10.0.0.0/19",<br>  "10.0.32.0/19",<br>  "10.0.64.0/19",<br>  "10.0.96.0/19"<br>]</pre> | no |
| <a name="input_public_subnets"></a> [public\_subnets](#input\_public\_subnets) | A list of public subnets CIDR range | `list` | <pre>[<br>  "10.0.128.0/20",<br>  "10.0.144.0/20",<br>  "10.0.160.0/20",<br>  "10.0.224.0/19"<br>]</pre> | no |
| <a name="input_region"></a> [region](#input\_region) | Region for the EKS deployment. | `string` | `"us-west-2"` | no |
| <a name="input_vpc_cidr"></a> [vpc\_cidr](#input\_vpc\_cidr) | The IPv4 CIDR block for the VPC. | `string` | `"10.0.0.0/16"` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_configure_kubectl"></a> [configure\_kubectl](#output\_configure\_kubectl) | Configure kubectl: make sure you're logged in with the correct AWS profile and run the following command to update your kubeconfig |
<!-- END_TF_DOCS -->