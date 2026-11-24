# EC2 Application Deployment Guide

## 1. Overview

The application is deployed on Amazon EC2 instances within the AWS VPC.

The deployment process uses an EC2 Launch Template and User Data script to automate instance initialization.

The Auto Scaling Group uses the Launch Template to launch and manage application instances.

## 2. Deployment Architecture

The application runs on EC2 instances in private subnets across two Availability Zones:

- `ap-south-1a`
- `ap-south-1b`

The Application Load Balancer receives incoming HTTP requests and forwards them to healthy application instances through the Target Group.

## 3. Instance Initialization

EC2 User Data is used to execute commands automatically when an instance launches.

The initialization process can install the required software, configure the web server, and prepare the application environment.

This reduces manual configuration and helps maintain consistency across instances.

## 4. Application Access

Users access the application through the Application Load Balancer DNS name.

The ALB forwards incoming requests to healthy EC2 instances registered in its Target Group.

Direct public access to the EC2 instances is restricted through Security Groups.

## 5. Auto Scaling Integration

The Auto Scaling Group uses the Launch Template to create additional EC2 instances when required.

New instances are configured using User Data and registered with the Target Group.

## 6. Shared Storage

Amazon EFS provides shared file storage for the EC2 instances.

The instances connect to EFS using NFS over TCP port `2049`.

## 7. Conclusion

The deployment process combines EC2, User Data, Launch Templates, Auto Scaling, the Application Load Balancer, and EFS to provide a consistent and scalable application environment.
