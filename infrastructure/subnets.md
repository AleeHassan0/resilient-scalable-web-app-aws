# AWS Subnets Configuration

## 1. Overview

Subnets are subdivisions of an Amazon Virtual Private Cloud (VPC) that allow network resources to be organized into separate segments.

In this project, subnets are used to separate public-facing infrastructure from private application resources.

The subnet architecture is deployed across two Availability Zones in the Asia Pacific (Mumbai) Region.

## 2. VPC Network

- **VPC CIDR:** `192.168.0.0/24`
- **AWS Region:** Asia Pacific (Mumbai)
- **Region Code:** `ap-south-1`

## 3. Subnet Configuration

The infrastructure contains four subnets distributed across two Availability Zones.

### Public Subnets

**public-subnet-1a**
- Availability Zone: `ap-south-1a`
- Type: Public Subnet
- Purpose: Hosts public-facing AWS resources.

**public-subnet-2b**
- Availability Zone: `ap-south-1b`
- Type: Public Subnet
- Purpose: Hosts public-facing AWS resources and supports multi-AZ infrastructure.

### Private Subnets

**private-subnet-1a**
- Availability Zone: `ap-south-1a`
- Type: Private Subnet
- Purpose: Hosts application resources without direct internet access.

**private-subnet-2b**
- Availability Zone: `ap-south-1b`
- Type: Private Subnet
- Purpose: Hosts application resources and supports availability across multiple AZs.

## 4. Public Subnets

Public subnets are associated with route tables that provide a route to the Internet Gateway.

These subnets are designed for resources that require inbound connectivity from the internet, such as the Application Load Balancer.

The public subnet architecture allows external users to access the application through the load balancer.

## 5. Private Subnets

Private subnets are used to deploy application resources that should not be directly accessible from the internet.

EC2 instances running the application are deployed in private subnets.

Outbound internet connectivity, when required, is provided through the NAT Gateway.

## 6. Multi-AZ Architecture

The subnets are distributed across two Availability Zones:

- `ap-south-1a`
- `ap-south-1b`

This architecture improves availability by distributing infrastructure across multiple Availability Zones.

If one Availability Zone experiences an issue, resources in the other Availability Zone may continue operating.

## 7. Security

The separation between public and private subnets helps improve network security.

Public-facing infrastructure is separated from application resources, while Security Groups control traffic between AWS resources.

## 8. Conclusion

The subnet architecture provides network segmentation, improved security, and multi-AZ deployment capabilities.

The four subnets form the networking foundation for the scalable and resilient AWS application architecture.
