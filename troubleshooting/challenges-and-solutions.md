# AWS Project Challenges and Solutions

## 1. Overview

During the implementation of the resilient and scalable AWS architecture, different configuration and deployment challenges were encountered.

This document records the problems, troubleshooting approaches, and solutions applied during the project.

## 2. Network Configuration

**Challenge:** Configuring public and private subnets across multiple Availability Zones.

**Solution:** Organized the VPC into separate public and private subnets across `ap-south-1a` and `ap-south-1b`, with route tables managing network connectivity.

## 3. Security Group Configuration

**Challenge:** Initial Security Group rules allowed unrestricted inbound traffic.

**Solution:** Removed unrestricted inbound rules and restricted access using specific ports and trusted Security Group references.

- ALB access: HTTP port 80.
- EC2 access: HTTP port 80 and TCP port 8080 from `ALB-SG`.
- EFS access: NFS port 2049 from `web-server-SG`.

## 4. Application Load Balancer Configuration

**Challenge:** Configuring the Application Load Balancer to communicate with the EC2 application instances.

**Solution:** Configured an HTTP listener and Target Group to forward requests to registered EC2 instances.

## 5. EC2 Deployment

**Challenge:** Ensuring EC2 instances are configured consistently when launched.

**Solution:** Used an EC2 Launch Template and User Data to automate instance initialization.

## 6. Shared Storage

**Challenge:** Providing shared file storage for multiple application instances.

**Solution:** Integrated Amazon EFS and configured NFS access through the EFS Security Group.

## 7. Conclusion

Working through these challenges provided practical experience with AWS networking, security, load balancing, automated deployment, and shared storage.

The project demonstrates the importance of troubleshooting and validating each infrastructure component.
