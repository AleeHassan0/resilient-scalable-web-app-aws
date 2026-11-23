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

## Application Traffic Flow

The application follows this traffic flow:

1. Internet users send HTTP requests to the application.
2. The requests enter the AWS VPC through the Internet Gateway.
3. The Application Load Balancer receives incoming traffic.
4. The Load Balancer forwards requests to the Target Group.
5. The Target Group routes requests to healthy EC2 instances registered within it.
6. The EC2 instances are managed by an Auto Scaling Group.
7. The application runs on EC2 instances deployed across multiple Availability Zones.
8. Amazon EFS provides shared storage to the EC2 instances.

This architecture allows incoming traffic to be distributed across multiple instances while providing scalability, high availability, and shared storage.

## AWS Services Used

## AWS Services Used

### Amazon VPC

Provides an isolated networking environment for the project infrastructure.

### Amazon EC2

Hosts the web application on virtual machines.

### Application Load Balancer (ALB)

Distributes incoming application traffic across registered EC2 instances.

### EC2 Auto Scaling Group

Automatically manages the number of EC2 instances based on the configured scaling policies and capacity settings.

### Amazon EFS

Provides shared file storage that can be accessed by multiple EC2 instances.

### Internet Gateway

Enables communication between the VPC and the internet.

### NAT Gateway

Provides outbound internet connectivity to resources located in private subnets.

### Security Groups

Control inbound and outbound traffic to AWS resources.

### Route Tables

Define network traffic routing within the VPC and between the VPC and external networks.

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


## Repository Structure

The repository is organized into the following directories and files:

- `README.md` — Main project overview and entry point.
- `architecture/` — Architecture diagrams and architecture documentation.
- `screenshots/` — Screenshots demonstrating the AWS infrastructure and application.
- `infrastructure/` — Documentation of AWS infrastructure components.
- `deployment/` — Deployment procedures and configuration details.
- `security/` — Security implementation and Security Group configurations.
- `testing/` — Testing procedures and results.
- `troubleshooting/` — Challenges encountered and their solutions.
- `scripts/` — Scripts used for deployment and configuration.




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



