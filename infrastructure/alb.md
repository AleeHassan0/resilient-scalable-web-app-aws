# Application Load Balancer Configuration

## 1. Overview

An Application Load Balancer (ALB) operates at the application layer (Layer 7) and distributes incoming HTTP and HTTPS traffic across multiple targets.

In this project, the ALB is used to distribute incoming application traffic across EC2 instances managed by an Auto Scaling Group.

It improves availability and helps prevent a single EC2 instance from becoming a bottleneck.

## 2. ALB Configuration

- **AWS Service:** Elastic Load Balancing
- **Load Balancer Type:** Application Load Balancer
- **Scheme:** Internet-facing
- **VPC:** `my-project-vpc`
- **AWS Region:** Asia Pacific (Mumbai)
- **Region Code:** `ap-south-1`
- **Availability Zones:** `ap-south-1a` and `ap-south-1b`
- **Security Group:** `ALB-SG`

## 3. Network Configuration

The Application Load Balancer is deployed across public subnets in two Availability Zones.

- `public-subnet-1a`
- `public-subnet-2b`

This allows the ALB to receive incoming traffic from the internet.

## 4. Listener Configuration

The ALB uses an HTTP listener to receive incoming requests.

### HTTP Listener

- **Protocol:** HTTP
- **Port:** `80`
- **Action:** Forward traffic to the configured Target Group.

The ALB Security Group allows HTTP traffic from the internet.

## 5. Target Group

The Target Group contains the EC2 instances that receive traffic forwarded by the ALB.

The Target Group is integrated with the Auto Scaling Group so that EC2 instances can be automatically registered and deregistered as instances are launched or terminated.

## 6. Health Checks

The ALB performs health checks on registered targets to determine whether they are healthy and capable of receiving traffic.

Unhealthy targets are excluded from normal traffic distribution until they become healthy again.



## 7. Traffic Distribution

Incoming requests follow this process:

1. A user sends an HTTP request to the ALB DNS name.
2. The ALB receives the request through its HTTP listener on port 80.
3. The listener forwards the request to the Target Group.
4. The Target Group selects a healthy EC2 instance.
5. The selected EC2 instance processes the request.
6. The response is returned to the user through the ALB.

## 8. High Availability

The ALB is deployed across multiple Availability Zones.

By distributing traffic across healthy EC2 instances in different Availability Zones, the architecture reduces dependency on a single instance or Availability Zone.

## 9. Security

The ALB uses the `ALB-SG` Security Group.

Inbound HTTP traffic is allowed from the internet on port 80.

Traffic to the EC2 instances is controlled through the `web-server-SG`, which allows application traffic only from the ALB Security Group.

This prevents direct public access to the application instances.

## 10. Conclusion

The Application Load Balancer provides a single entry point for the application.

It distributes traffic across healthy EC2 instances, supports high availability, and works with the Auto Scaling Group to provide a scalable application architecture.
