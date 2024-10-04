---
# AWS VPC with EC2 Instances - Terraform Setup

This Terraform configuration creates an AWS VPC with both public and private subnets, sets up necessary routing, security groups, and provisions EC2 instances. The public instance hosts a web server, while the private instance simulates a database server.

## Features

- **VPC Creation**: A new VPC is created in the `ap-south-1` region with DNS hostnames enabled.
- **Subnets**: 
  - Public subnet in the first availability zone.
  - Private subnet in the second availability zone.
- **Internet Gateway**: Enables internet connectivity for the public subnet.
- **Route Tables**:
  - Public route table associated with the public subnet.
  - Private route table associated with the private subnet.
- **Security Groups**:
  - Web server instance security group allows SSH (port 22) and HTTP (port 8080) traffic.
  - Database instance security group allows MySQL (port 3306) traffic between the web server and database instances.
- **EC2 Instances**:
  - Public instance running a basic web server on port 8080.
  - Private instance simulating a database server, accessible only by the public instance.

## Resources Created

- VPC
- Public and Private Subnets
- Internet Gateway
- Public and Private Route Tables
- EC2 Instances:
  - Public Web Server
  - Private Database Server
- Security Groups for the EC2 instances

## Requirements

- **Terraform**: v0.12+
- **AWS CLI**: To authenticate and manage AWS services.
- **AWS Account**: Ensure valid credentials with access to create VPC, EC2, etc.

## Variables

| Variable     | Default Value          | Description                       |
|--------------|------------------------|-----------------------------------|
| `vpc_cidr`   | `"10.0.0.0/16"`        | CIDR block for the VPC            |
| `subnet1_cidr` | `"10.0.0.0/24"`       | CIDR block for the public subnet  |
| `subnet2_cidr` | `"10.0.1.0/24"`       | CIDR block for the private subnet |
| `amiid`      | `"ami-0d758c1134823146a"` | AMI ID for the EC2 instances      |
| `type`       | `"t2.micro"`           | EC2 instance type                 |
| `pemfile`    | `"JanFeb24"`           | PEM file for SSH access           |

## Usage

1. **Clone this repository**:
   ```bash
   git clone https://github.com/yourusername/your-repo-name.git
   cd your-repo-name
   ```

2. **Initialize Terraform**:
   ```bash
   terraform init
   ```

3. **Apply the Terraform configuration**:
   ```bash
   terraform apply
   ```

4. **Check Output**: After running, the web server can be accessed on port 8080 of the EC2 instance's public IP address.

---
