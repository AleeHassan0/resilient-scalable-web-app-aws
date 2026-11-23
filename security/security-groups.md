# AWS Security Groups Configuration

## 1. Overview

Security Groups act as virtual firewalls that control inbound and outbound traffic for AWS resources.

In this project, Security Groups are used to secure the Application Load Balancer, EC2 web servers, and Amazon EFS by restricting traffic to specific sources and ports.


## 2. Security Architecture

The project uses three Security Groups:

- `ALB-SG`
- `web-server-SG`
- `EFS-SG`

Each Security Group controls traffic for a specific infrastructure component.

## 3. ALB-SG

The ALB Security Group controls inbound traffic to the Application Load Balancer.

### Inbound Rules

**Rule 1: HTTP**

- Type: HTTP
- Protocol: TCP
- Port: `80`
- Source: `0.0.0.0/0`
- Purpose: Allows users to access the application through the Application Load Balancer.

**Rule 2: Custom TCP**

- Type: Custom TCP
- Port: `8080`
- Source: My IP
- Purpose: Allows restricted access from the administrator's IP address for testing.


## 4. web-server-SG

The Web Server Security Group controls inbound traffic to the EC2 instances hosting the application.

### Inbound Rules

**Rule 1: HTTP**

- Type: HTTP
- Protocol: TCP
- Port: `80`
- Source: `ALB-SG`
- Purpose: Allows HTTP traffic from the Application Load Balancer.

**Rule 2: Custom TCP**

- Type: Custom TCP
- Protocol: TCP
- Port: `8080`
- Source: `ALB-SG`
- Purpose: Allows the Application Load Balancer to access the test application running on port 8080.

Direct access from the internet is not permitted.


## 5. EFS-SG

The EFS Security Group controls network access to Amazon Elastic File System.

### Inbound Rules

**Rule: NFS**

- Type: NFS
- Protocol: TCP
- Port: `2049`
- Source: `web-server-SG`
- Purpose: Allows EC2 web servers to connect to and access the shared EFS file system.

Access is restricted to the Web Server Security Group.

## 6. Security Improvements

The security configuration was improved through the following changes:

- Removed unrestricted inbound traffic from the ALB Security Group.
- Allowed HTTP traffic on port 80 to the Application Load Balancer.
- Restricted port 8080 access on the ALB to the administrator's IP.
- Removed unrestricted inbound access from EC2 instances.
- Allowed EC2 application traffic only from the ALB Security Group.
- Restricted EFS access to EC2 web servers.
- Used Security Group references instead of allowing traffic from all IP addresses.

## 7. Traffic Flow

Users access the application through the Application Load Balancer on HTTP port 80.

The ALB forwards requests to the EC2 instances through the Web Server Security Group.

The EC2 instances communicate with Amazon EFS through NFS port 2049.

The Security Groups ensure that each component accepts traffic only from its permitted source.

## 8. Conclusion

The Security Group configuration follows the principle of least privilege by restricting network access to the required ports and trusted sources.

This improves the security of the AWS architecture and prevents direct unauthorized access to the EC2 instances and EFS.
