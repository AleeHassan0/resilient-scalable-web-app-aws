# AWS Project Testing and Results

## 1. Overview

Testing was performed to verify the functionality, availability, security, and scalability of the AWS application infrastructure.

The tests focus on the Application Load Balancer, EC2 instances, Auto Scaling Group, Security Groups, and Amazon EFS.

## 2. Application Load Balancer Testing

**Objective:** Verify that users can access the application through the Application Load Balancer.

**Test procedure:**
- Open the ALB DNS name in a web browser.
- Send an HTTP request to the application.
- Verify that the application responds successfully.

**Result:** it was working

## 3. EC2 Instance Testing

**Objective:** Verify that the application is running correctly on EC2 instances.

**Test procedure:**
- Check the EC2 instance state.
- Connect to an instance when required.
- Verify that the web server is installed and running.
- Test application access through the ALB.



## 4. Auto Scaling Testing

**Objective:** Verify that the Auto Scaling Group can adjust EC2 capacity.

**Test procedure:**
- Monitor the Auto Scaling Group.
- Check the number of running instances.
- Verify instance launch and termination behavior according to the configured scaling policy.

**Result:** i terminated one instance it created a new one.

## 5. Security Group Testing

**Objective:** Verify that network access is restricted according to the configured Security Group rules.

**Test procedure:**
- Verify that HTTP traffic reaches the ALB.
- Verify that EC2 application traffic is allowed from the ALB Security Group.
- Verify that EFS accepts NFS traffic from the Web Server Security Group.
- Check that direct public access to EC2 instances is restricted.



## 6. Amazon EFS Testing

**Objective:** Verify that EC2 instances can access shared storage.

**Test procedure:**
- Check the EFS mount status on EC2 instances.
- Create a test file through one instance.
- Verify whether another instance can access the same file.



## 7. Conclusion

Testing helps verify that the AWS infrastructure operates according to the intended architecture.

