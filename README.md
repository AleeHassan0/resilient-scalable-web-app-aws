# Resilient and Scalable Web Application Deployment on AWS

## Project Overview

This project demonstrates the design and deployment of a resilient, highly available, and scalable web application infrastructure using Amazon Web Services (AWS).

The infrastructure is designed to distribute incoming application traffic across multiple EC2 instances using an Application Load Balancer. Amazon EC2 Auto Scaling is used to manage the compute capacity of the application, while Amazon EFS provides shared storage for the EC2 instances.

The project follows AWS cloud architecture principles, including high availability, scalability, network isolation, and security.

---

## Project Objectives

- Design a highly available cloud infrastructure.
- Deploy resources across multiple Availability Zones.
- Distribute application traffic using an Application Load Balancer.
- Implement automatic scaling using an EC2 Auto Scaling Group.
- Configure shared storage using Amazon EFS.
- Separate public and private network resources.
- Implement network security using Security Groups.
- Understand the deployment, operation, and troubleshooting of AWS infrastructure.

---

## Architecture Overview

The infrastructure is deployed within an Amazon VPC in the US East (N. Virginia) region.

The architecture includes public and private subnets distributed across multiple Availability Zones.

### Application Traffic Flow


Internet Users
      |
      v
Internet Gateway
      |
      v
Application Load Balancer
      |
      v
Target Group
      |
      v
EC2 Auto Scaling Group
      |
      +-------------------+
      |                   |
      v                   v
EC2 Instance 1       EC2 Instance 2
      |                   |
      +---------+---------+
                |
                v
             Amazon EFS




## AWS Services Used

| AWS Service | Purpose |
|
| Amazon VPC | Provides an isolated networking environment |
| Amazon EC2 | Hosts the web application |
| Application Load Balancer | Distributes incoming application traffic |
| EC2 Auto Scaling | Automatically manages EC2 instance capacity |
| Amazon EFS | Provides shared file storage |
| Internet Gateway | Enables internet connectivity for the VPC |
| NAT Gateway | Enables outbound internet access from private resources |
| Security Groups | Controls inbound and outbound network traffic |
| Route Tables | Controls network traffic routing |

---

## Key Features

- High availability across multiple Availability Zones
- Load balancing across EC2 instances
- Automatic scaling of compute resources
- Shared storage using Amazon EFS
- Public and private subnet architecture
- Network traffic control using Security Groups
- Automated EC2 configuration using Launch Templates and User Data

---

## Repository Structure


resilient-scalable-web-app-aws/
│
├── README.md
│
├── architecture/
│   ├── architecture-diagram.png
│   └── architecture.md
│
├── screenshots/
│
├── infrastructure/
│
├── deployment/
│
├── security/
│
├── testing/
│
├── troubleshooting/
│
└── scripts/




## Architecture Documentation

Detailed documentation of the infrastructure components will be available in the following sections:

- [Architecture Overview](architecture/architecture.md)
- VPC and Networking
- Subnets and Availability Zones
- Route Tables
- Internet Gateway
- NAT Gateway
- Security Groups
- Application Load Balancer
- EC2 Auto Scaling
- Amazon EFS



## Deployment

The deployment documentation will explain the implementation process, including:

1. VPC configuration
2. Subnet creation
3. Routing configuration
4. Security Group configuration
5. EC2 configuration
6. Application Load Balancer setup
7. Auto Scaling configuration
8. Amazon EFS integration
9. Application testing

---

## Testing and Validation

The infrastructure will be validated through:

- Application accessibility through the Load Balancer
- Target Group health checks
- EC2 instance status
- Auto Scaling functionality
- EFS connectivity and shared storage
- Network connectivity and security validation

Actual test results and screenshots will be documented in the repository.

---

## Challenges and Troubleshooting

Technical challenges encountered during the implementation, their root causes, and the solutions applied will be documented in the troubleshooting section.



