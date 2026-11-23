# Internet Gateway Configuration

## 1. Overview

An Internet Gateway (IGW) is an AWS networking component that allows communication between resources in a VPC and the internet.

It provides internet connectivity to resources located in public subnets when the appropriate routing and security rules are configured.

## 2. Internet Gateway Configuration

- **AWS Service:** Amazon VPC
- **Component:** Internet Gateway
- **VPC:** my-project-vpc
- **AWS Region:** Asia Pacific (Mumbai)
- **Region Code:** `ap-south-1`

## 3. Purpose

The Internet Gateway was created to provide internet connectivity to the public subnets within the VPC.

It enables internet-facing resources, such as the Application Load Balancer, to receive traffic from external users.

## 4. Connectivity

The Internet Gateway is attached to the custom VPC.

Public subnet route tables use the Internet Gateway as the target for internet-bound traffic.

The default route is:

- **Destination:** `0.0.0.0/0`
- **Target:** Internet Gateway

## 5. Traffic Flow

Internet traffic reaches the VPC through the Internet Gateway.

The Application Load Balancer receives incoming HTTP requests from users and forwards traffic to the application instances through the configured Target Group.

## 6. Security

The Internet Gateway itself does not provide traffic filtering.

Security Groups and routing configurations are used to control which resources can receive or initiate network traffic.

## 7. Conclusion

The Internet Gateway provides the connection between the VPC and the internet, enabling external users to access the application through the public-facing infrastructure.
