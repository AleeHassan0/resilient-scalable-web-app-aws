# Amazon EFS Configuration

## 1. Overview

Amazon Elastic File System (EFS) provides scalable, shared file storage for AWS workloads.

In this project, EFS is used to provide shared storage for EC2 web server instances managed by the Auto Scaling Group.

Multiple EC2 instances can access the same file system, allowing them to share application files and data.

## 2. EFS Configuration

- **AWS Service:** Amazon Elastic File System
- **VPC:** `my-project-vpc`
- **AWS Region:** Asia Pacific (Mumbai)
- **Region Code:** `ap-south-1`
- **Security Group:** `EFS-SG`
- **Network Protocol:** NFS
- **Port:** `2049`

## 3. Shared Storage

EFS provides a shared file system that can be mounted by multiple EC2 instances.

When multiple application instances use the same EFS file system, they can access shared files instead of maintaining separate copies on each instance.

This is particularly useful in an Auto Scaling environment where new EC2 instances may be launched automatically.

## 4. Network Configuration

The EFS file system uses mount targets to provide network access from the VPC.

The EC2 instances connect to EFS using the Network File System (NFS) protocol.

- **Protocol:** TCP
- **Port:** `2049`
- **Source Security Group:** `web-server-SG`
- **Destination Security Group:** `EFS-SG`

## 5. Security Configuration

The EFS Security Group allows inbound NFS traffic only from `web-server-SG`.

This ensures that only authorized web server instances can connect to the file system.

Unrestricted inbound access from the internet is not allowed.

## 6. Integration with Auto Scaling

The EC2 instances managed by the Auto Scaling Group can mount the shared EFS file system.

This allows application instances to access common files even when the Auto Scaling Group launches additional instances.

## 7. Benefits

- Shared storage across multiple EC2 instances.
- Scalable file storage.
- Supports application consistency across instances.
- Useful for Auto Scaling environments.
- Centralized file storage management.

## 8. Conclusion

Amazon EFS provides shared storage for the application infrastructure.

By connecting multiple EC2 instances to the same file system, EFS supports consistent file access and improves the architecture's ability to scale.
