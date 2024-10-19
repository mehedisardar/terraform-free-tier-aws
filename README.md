# AWS Infrastructure Deployment with Terraform

This Terraform configuration deploys a basic AWS infrastructure including a VPC, subnets, an internet gateway, route tables, a security group, network interfaces, an Elastic IP, and an EC2 instance with a simple web server. It is structured for a production environment in the AWS region `eu-west-2`.

<p>
<img alt="GitHub Contributors" src="https://img.shields.io/github/contributors/mehedisardar/terraform-free-tier-aws" />
<img alt="GitHub Last Commit" src="https://img.shields.io/github/last-commit/mehedisardar/terraform-free-tier-aws" />
<img alt="" src="https://img.shields.io/github/repo-size/mehedisardar/terraform-free-tier-aws" />
<img alt="GitHub Issues" src="https://img.shields.io/github/issues/mehedisardar/terraform-free-tier-aws" />
<img alt="GitHub Pull Requests" src="https://img.shields.io/github/issues-pr/mehedisardar/terraform-free-tier-aws" />
<img alt="Github License" src="https://img.shields.io/github/license/mehedisardar/terraform-free-tier-aws" />
</p>

## Prerequisites

Before you begin, ensure you have the following:

- Terraform installed on your machine.
- An AWS account with the necessary permissions to create the resources.
- AWS CLI configured with appropriate credentials.

## Configuration Details

The infrastructure includes:

- **VPC**: A Virtual Private Cloud configured with a CIDR block of `10.0.0.0/16`.
- **Internet Gateway**: Provides a gateway for communication between resources in the VPC and the internet.
- **Route Tables**: Routes traffic within the VPC and to the internet.
- **Subnets**: A subnet within the VPC with a CIDR block of `10.0.1.0/24`.
- **Security Group**: Configures rules for inbound and outbound traffic to control access to EC2 instances.
- **Network Interface**: Associates with the EC2 instance to facilitate network connectivity.
- **Elastic IP**: Provides a static IPv4 address for your instance, ensuring it remains constant even if the instance is stopped and restarted.
- **EC2 Instance**: A `t2.micro` instance using an AMI (`ami-09627c82937ccdd6d`) pre-configured to run a basic web server using Apache.

### Security

This configuration opens SSH (port 22), HTTP (port 80), and HTTPS (port 443) to all traffic (0.0.0.0/0). Please adjust the CIDR blocks in the security group settings according to your security requirements.

## Reminder

1. Replace placeholder values in the provider block with your AWS access and secret keys:

   ```hcl
   provider "aws" {
     region     = "eu-west-2"
     access_key = "insert your key here"
     secret_key = "insert your key here"
   }
