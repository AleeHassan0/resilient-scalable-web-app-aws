# AWS Route Tables Configuration

## 1. Overview

Route tables control how network traffic is directed within an Amazon Virtual Private Cloud (VPC).

In this project, route tables are used to manage traffic between public and private subnets, the Internet Gateway, and the NAT Gateway.

The VPC uses two route tables:

- Public Route Table
- Main Route Table

## 2. Public Route Table

The Public Route Table is associated with both public subnets.

### Subnet Associations

- `public-subnet-1a` — `ap-south-1a`
- `public-subnet-2b` — `ap-south-1b`

### Internet Connectivity

The Public Route Table contains a default route directing internet-bound traffic to the Internet Gateway.

- **Destination:** `0.0.0.0/0`
- **Target:** Internet Gateway

This allows resources in the public subnets to communicate with the internet when their configurations permit it.

## 3. Main Route Table

The Main Route Table is associated with both private subnets.

### Subnet Associations

- `private-subnet-1a` — `ap-south-1a`
- `private-subnet-2b` — `ap-south-1b`

### Internet Connectivity

The Main Route Table directs internet-bound traffic through the NAT Gateway located in `public-subnet-1a`.

- **Destination:** `0.0.0.0/0`
- **Target:** NAT Gateway

This allows resources in the private subnets to initiate outbound internet connections without being directly exposed to inbound internet traffic.

## 4. Traffic Routing

### Public Subnet Traffic

Traffic from the public subnets destined for the internet is routed through the Internet Gateway.

The public route table is shared by both public subnets across the two Availability Zones.

### Private Subnet Traffic

Traffic from the private subnets destined for the internet is routed through the NAT Gateway.

The Main Route Table is associated with both private subnets.

## 5. Route Table Associations

### Public Route Table

Associated subnets:

- `public-subnet-1a`
- `public-subnet-2b`

### Main Route Table

Associated subnets:

- `private-subnet-1a`
- `private-subnet-2b`

## 6. Security

Route tables determine traffic paths but do not filter traffic.

Security Groups are used to control permitted inbound and outbound traffic for AWS resources.

The separation of public and private subnets helps prevent direct internet access to private application resources.

## 7. Conclusion

The route table configuration provides connectivity for public resources through the Internet Gateway and outbound internet access for private resources through the NAT Gateway.

This configuration supports network segmentation and the security of the application infrastructure.
