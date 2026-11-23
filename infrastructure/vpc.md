# Amazon VPC Configuration

## 1. Overview

Amazon Virtual Private Cloud (VPC) provides a logically isolated network environment for deploying and managing AWS resources.

For this project, a custom VPC was created to host the application's networking infrastructure, including subnets, EC2 instances, the Application Load Balancer, and other AWS services.

## 2. VPC Configuration

- **AWS Region:** Asia Pacific (Mumbai)
- **Region Code:** `ap-south-1`
- **VPC Name:** My-project-vpc
- **IPv4 CIDR Block:** 192.168.0.0/24

## 3. Purpose of the VPC

The VPC provides the networking foundation for the application. It allows AWS resources to communicate with each other while controlling network access through subnet configurations, route tables, and security groups.

The network was designed to separate public-facing resources from application resources to improve security and architecture organization.

## 4. Availability Zones

The infrastructure is deployed across two Availability Zones in the Mumbai Region:

- `ap-south-1a`
- `ap-south-1b`

Using multiple Availability Zones helps improve availability and provides redundancy in case one Availability Zone experiences an issue.

## 5. Network Components

The VPC contains the following networking components:

- Public Subnets
- Private Subnets
- Internet Gateway
- NAT Gateway
- Route Tables
- Security Groups

These components work together to provide network connectivity, internet access where required, and controlled communication between resources.

## 6. Security

The VPC uses subnet separation and security groups to control network traffic.

Public-facing components are separated from application resources, and network access is restricted according to the requirements of each component.

## 7. Conclusion

The custom VPC provides the foundation for the resilient and scalable AWS architecture. It enables network isolation, controlled communication, and deployment across multiple Availability Zones.
