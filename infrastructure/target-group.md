# AWS Target Group Configuration

## 1. Overview

An AWS Target Group is used by a Load Balancer to route incoming requests to registered targets.

In this project, the Target Group connects the Application Load Balancer to the EC2 web server instances.

## 2. Target Group Configuration

- **AWS Service:** Elastic Load Balancing
- **Target Type:** Instances
- **VPC:** `my-project-vpc`
- **AWS Region:** Asia Pacific (Mumbai)
- **Region Code:** `ap-south-1`

## 3. Traffic Configuration

The Target Group receives traffic forwarded by the Application Load Balancer.

- **Application Protocol:** HTTP
- **Application Port:** 
- **Load Balancer:** Application Load Balancer
- **Registered Targets:** EC2 web server instances

## 4. Health Checks

The Target Group periodically checks the health of registered EC2 instances.

Health checks help the Load Balancer identify healthy instances and avoid sending normal application traffic to unhealthy targets.

The actual health check path, port, and thresholds should be documented from the AWS console.

## 5. Auto Scaling Integration

The Target Group is associated with the EC2 Auto Scaling Group.

When the Auto Scaling Group launches a new EC2 instance, it can automatically register that instance with the Target Group.

When an instance is terminated, it is deregistered.

## 6. Traffic Flow

1. A user sends an HTTP request to the Application Load Balancer.
2. The ALB listener receives the request.
3. The listener forwards the request to the Target Group.
4. The Target Group selects a healthy registered EC2 instance.
5. The EC2 instance processes the request.
6. The response returns through the Application Load Balancer.

## 7. Conclusion

The Target Group connects the Application Load Balancer with the EC2 application instances.

Its health checks and integration with Auto Scaling help maintain application availability as instances change.
