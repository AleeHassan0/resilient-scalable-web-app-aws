# EC2 Auto Scaling Group Configuration

## 1. Overview

Amazon EC2 Auto Scaling helps maintain application availability by automatically adjusting the number of EC2 instances according to defined scaling requirements.

In this project, an Auto Scaling Group manages the EC2 web server instances behind the Application Load Balancer.

## 2. Auto Scaling Group Configuration

- **AWS Service:** Amazon EC2 Auto Scaling
- **VPC:** `my-project-vpc`
- **AWS Region:** Asia Pacific (Mumbai)
- **Region Code:** `ap-south-1`
- **Availability Zones:** `ap-south-1a` and `ap-south-1b`
- **Launch Template:** Used to configure new EC2 instances
- **Target Group:** Connected to the Application Load Balancer

## 3. Launch Template Integration

The Auto Scaling Group uses an EC2 Launch Template to create new instances.

The Launch Template defines the AMI, instance type, security group, storage configuration, and User Data script.

This ensures that newly launched instances use a consistent configuration.

## 4. Capacity Configuration

The Auto Scaling Group uses three capacity settings:

- **Minimum Capacity:** [Add actual value]
- **Desired Capacity:** [Add actual value]
- **Maximum Capacity:** [Add actual value]

The minimum capacity defines the lowest number of instances to maintain.

The desired capacity defines the intended number of running instances.

The maximum capacity defines the upper limit of instances the group can launch.

## 5. Multi-AZ Deployment

The Auto Scaling Group is configured to use subnets across two Availability Zones:

- `ap-south-1a`
- `ap-south-1b`

Distributing instances across multiple Availability Zones improves application availability.

## 6. Load Balancer Integration

The Auto Scaling Group is associated with the Application Load Balancer Target Group.

New instances are registered with the Target Group, allowing the Load Balancer to send traffic to healthy instances.

Instances that are terminated are removed from the Target Group.

## 7. Dynamic Scaling

Dynamic scaling policies allow the Auto Scaling Group to adjust the number of EC2 instances based on monitored conditions.

For example, when application demand increases, the group can launch additional instances.

When demand decreases, it can reduce the number of instances according to the configured scaling policy.

## 8. Benefits

- Automatic capacity adjustment.
- Improved application availability.
- Consistent instance configuration.
- Multi-AZ deployment.
- Integration with the Application Load Balancer.
- Reduced manual instance management.

## 9. Conclusion

The Auto Scaling Group helps maintain application capacity and availability by managing EC2 instances automatically.

Together with the Launch Template and Application Load Balancer, it forms an important part of the scalable AWS architecture.
