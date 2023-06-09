# Provisioning a Jenkins Server with Terraform

This repository contains Terraform code to provision a Jenkins server in AWS. The infrastructure is defined as code, which allows for easy deployment, versioning, and collaboration.

## Prerequisites

Before running the Terraform code, ensure that the following prerequisites are met:
- AWS account
- Terraform installed on your local machine
- AWS CLI installed and configured on your local machine
- SSH key pair generated

## Usage

To provision the Jenkins server, follow these steps:

1. Clone this repository to your local machine.
2. Navigate to the directory containing the `main.tf` file.
3. Run `terraform init` to initialize the Terraform configuration.
4. Run `terraform apply` to create the infrastructure.
5. SSH into the Jenkins server using the public IP address and your SSH key pair.

## Customization

This Terraform code can be customized to fit your specific requirements. Some of the variables that can be changed include:
- Instance type
- Region
- VPC configuration
- Security groups

## Cleanup

To remove the infrastructure created by this Terraform code, run `terraform destroy`.


## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.3.9 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | ~> 4.0 |
| <a name="requirement_template"></a> [template](#requirement\_template) | 2.2.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | 4.66.1 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_vpc"></a> [vpc](#module\_vpc) | terraform-aws-modules/vpc/aws | 4.0.1 |

## Resources

| Name | Type |
|------|------|
| [aws_eip.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/eip) | resource |
| [aws_eip_association.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/eip_association) | resource |
| [aws_iam_instance_profile.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_instance_profile) | resource |
| [aws_iam_role.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role) | resource |
| [aws_iam_role_policy.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role_policy) | resource |
| [aws_iam_role_policy_attachment.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role_policy_attachment) | resource |
| [aws_instance.jenkins_server](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/instance) | resource |
| [aws_security_group.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group) | resource |
| [aws_ami.amazon_linux_x86_64](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/ami) | data source |
| [aws_availability_zones.available](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/availability_zones) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_instance_type"></a> [instance\_type](#input\_instance\_type) | Server instance type | `string` | n/a | yes |
| <a name="input_prefix"></a> [prefix](#input\_prefix) | Prefix used to compose the resouces names | `string` | n/a | yes |
| <a name="input_ssh_user"></a> [ssh\_user](#input\_ssh\_user) | Default SSH user for this AMI. e.g. `ec2-user` for Amazon Linux and `ubuntu` for Ubuntu systems | `string` | n/a | yes |
| <a name="input_user_data"></a> [user\_data](#input\_user\_data) | User data content. Will be ignored if `user_data_base64` is set | `list(string)` | `[]` | no |
| <a name="input_user_data_template"></a> [user\_data\_template](#input\_user\_data\_template) | User Data template to use for provisioning Pritunl server | `string` | n/a | yes |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_public_ip"></a> [public\_ip](#output\_public\_ip) | The public IP address of the Jenkins server |
| <a name="output_sg_id"></a> [sg\_id](#output\_sg\_id) | The ID of the security group |
| <a name="output_vpc_id"></a> [vpc\_id](#output\_vpc\_id) | ID of the VPC |

## Contributing

If you find any issues or would like to contribute to this project, please feel free to submit a pull request.
