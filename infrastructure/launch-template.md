# EC2 Launch Template Configuration

## 1. Overview

An Amazon EC2 Launch Template contains the configuration required to launch EC2 instances.

In this project, the Launch Template is used by the Auto Scaling Group to create application instances with consistent configurations.

## 2. Launch Template Configuration

- **AWS Service:** Amazon EC2
- **Component:** Launch Template
- **VPC:** `my-project-vpc`
- **AWS Region:** Asia Pacific (Mumbai)
- **Region Code:** `ap-south-1`

## 3. Instance Configuration

The Launch Template defines the settings used when creating EC2 instances.

These settings include:

- Amazon Machine Image (AMI)
- Instance Type
- Key Pair
- Security Group: `web-server-SG`
- Storage Configuration
- User Data Script

## 4. User Data Script

User Data is used to automate instance initialization when an EC2 instance launches.

It can install required software, configure the web server, and deploy the application automatically.

This reduces the need for manual configuration on every new instance.

## 5. Auto Scaling Integration

The Auto Scaling Group uses this Launch Template to launch new EC2 instances.

When additional application capacity is required, the Auto Scaling Group creates instances using the configuration defined in the template.

This ensures consistency across application instances.

## 6. Benefits

- Consistent EC2 instance configuration.
- Automated instance initialization.
- Easier scaling.
- Reduced manual configuration.
- Repeatable application deployment.

## 7. Conclusion

The EC2 Launch Template provides a reusable configuration for application instances and supports automated scaling through the Auto Scaling Group.
