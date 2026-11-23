# AWS Architecture Documentation

## 1. Architecture Overview

This project implements a resilient and scalable web application infrastructure using Amazon Web Services (AWS).

The infrastructure is designed to provide high availability, scalability, fault tolerance, and secure network communication. The application is deployed on Amazon EC2 instances managed by an EC2 Auto Scaling Group. An Application Load Balancer distributes incoming traffic across the application instances, while Amazon EFS provides shared storage.

The infrastructure is deployed inside an Amazon Virtual Private Cloud (VPC), with resources distributed across multiple Availability Zones to improve availability and resilience.

## 2. AWS Region

The project is deployed in the Asia Pacific (Mumbai) region.

AWS Region: Asia Pacific (Mumbai)

Region Code: ap-south-1

The selected region provides access to the AWS services required for the project.

## 3. Architecture Components

### Amazon Virtual Private Cloud (VPC)

Amazon VPC provides an isolated networking environment for the project's AWS resources.

The VPC contains public and private subnets, route tables, network gateways, and security configurations required for communication between infrastructure components.

### Availability Zones

The infrastructure is deployed across two Availability Zones within the Asia Pacific (Mumbai) region.

- Availability Zone 1: ap-south-1a
- Availability Zone 2: ap-south-1b

Deploying resources across multiple Availability Zones helps improve availability and resilience by reducing dependency on a single Availability Zone.

The Application Load Balancer and application infrastructure are configured to support traffic distribution across the two Availability Zones.

### Public Subnets

Public subnets contain resources that require connectivity with the internet or receive incoming internet traffic.

The public subnet architecture supports the deployment of the Application Load Balancer and networking components.

### Private Subnets

Private subnets are used to host the application EC2 instances.

The instances are not directly exposed to incoming internet traffic. Application traffic is received through the Application Load Balancer.

### Internet Gateway

The Internet Gateway provides connectivity between the VPC and the internet.

It enables internet communication for resources that have appropriate routing and network configurations.

### NAT Gateway

The NAT Gateway enables resources located in private subnets to initiate outbound internet connections without requiring direct inbound internet connectivity.

It supports outbound communication required by private resources.

### Application Load Balancer

The Application Load Balancer receives incoming application traffic and distributes requests across registered EC2 instances.

It uses a Target Group and health checks to identify healthy application instances and route traffic accordingly.

### EC2 Auto Scaling Group

The EC2 Auto Scaling Group manages the EC2 instances hosting the application.

It maintains the configured capacity of the application infrastructure and can launch or terminate instances according to its configuration and scaling policies.

### Amazon EC2

Amazon EC2 provides the compute capacity required to host the web application.

The instances are deployed within private subnets and receive application traffic through the Application Load Balancer.

### Amazon Elastic File System (EFS)

Amazon EFS provides shared file storage for the application instances.

Multiple EC2 instances can access the shared file system, allowing application data stored on EFS to be accessible across the instances.

## 4. Application Traffic Flow

The application follows the traffic flow described below:

1. Internet users send requests to the web application.
2. Incoming traffic reaches the VPC through the Internet Gateway.
3. The Application Load Balancer receives the application traffic.
4. The Load Balancer forwards requests to the configured Target Group.
5. The Target Group directs requests to healthy EC2 instances.
6. The EC2 instances are managed by the Auto Scaling Group.
7. The application runs on EC2 instances deployed within private subnets.
8. Amazon EFS provides shared storage accessible by the application instances.

## 5. High Availability

High availability is supported through the deployment of infrastructure across multiple Availability Zones.

The Application Load Balancer distributes application traffic across available healthy targets.

The Auto Scaling Group manages the application instance capacity and helps maintain the required number of EC2 instances.

This architecture reduces dependency on a single EC2 instance and supports continued application availability when individual instances become unavailable.

## 6. Scalability

The project uses EC2 Auto Scaling to manage application compute capacity.

The Auto Scaling Group can adjust the number of EC2 instances according to its configured capacity and scaling policies.

The Application Load Balancer distributes incoming traffic across the available application instances.

Together, these services support the scalability of the application infrastructure.

## 7. Shared Storage

Amazon EFS is integrated into the architecture to provide shared file storage.

The file system can be accessed by multiple EC2 instances, allowing shared application files to be available across the instances.

This reduces dependency on storage located on a single EC2 instance.

## 8. Security Architecture

The infrastructure uses Security Groups to control network traffic between AWS resources.

The architecture separates public-facing networking components from application instances hosted within private subnets.

The Application Load Balancer acts as the entry point for application traffic, while the EC2 instances are configured to receive traffic according to their Security Group rules.

## 9. Architecture Diagram

The architecture diagram illustrates the relationship between the VPC, public and private subnets, Internet Gateway, NAT Gateway, Application Load Balancer, EC2 Auto Scaling Group, EC2 instances, and Amazon EFS.

The diagram is available in the architecture directory of this repository.

## 10. Conclusion

The architecture combines AWS networking, load balancing, automatic scaling, and shared storage to provide a resilient and scalable web application infrastructure.

The implementation demonstrates practical experience with AWS cloud architecture, network design, compute services, availability, scalability, and infrastructure security.
