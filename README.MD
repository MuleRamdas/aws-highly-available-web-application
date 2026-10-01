Create a professional GitHub README.md for my AWS project.

Project Name:
AWS Highly Available Web Application using ALB and Auto Scaling

Project Objective:
Build a highly available and scalable web application on AWS using
Amazon VPC, Availability Zones, Public and Private Subnets,
Internet Gateway, NAT Gateway, Application Load Balancer,
Target Group, Launch Template, EC2, and Auto Scaling Group.

AWS Architecture:

VPC:
- Name: project3-q3-vpc
- CIDR: 10.0.0.0/16

Availability Zones:
- ap-south-1a
- ap-south-1b

Public Subnets:
- public-subnet-az1: 10.0.1.0/24
- public-subnet-az2: 10.0.3.0/24

Private Subnets:
- private-subnet-az1: 10.0.2.0/24
- private-subnet-az2: 10.0.4.0/24

Internet Gateway:
- project3-q3-igw

NAT Gateway:
- project3-q3-nat-gateway

Public Route Table:
- project3-q3-public-rt
- Route: 0.0.0.0/0 → Internet Gateway

Private Route Table:
- project3-q3-private-rt
- Route: 0.0.0.0/0 → NAT Gateway

Application Load Balancer:
- Name: project3-q3-alb
- Type: Internet-facing
- Listener: HTTP : 80
- Availability Zones: ap-south-1a and ap-south-1b

Target Group:
- Name: project3-q3-target-group
- Target Type: Instance
- Protocol: HTTP
- Port: 80
- Health Check Path: /
- Success Code: 200

Launch Template:
- Name: project3-q3-launch-template
- AMI: Amazon Linux 2023
- Instance Type: t3.micro
- Key Pair: mumbairesion
- Security Group: project3-q3-ec2-sg
- Apache HTTP Server installed using User Data

User Data:

#!/bin/bash
dnf update -y
dnf install -y httpd
systemctl enable httpd
systemctl start httpd

echo "<h1>Q3 AWS Auto Scaling Web Application</h1>" > /var/www/html/index.html
echo "<p>Server: $(hostname)</p>" >> /var/www/html/index.html

Auto Scaling Group:
- Name: project3-q3-vpc
- Desired Capacity: 2
- Minimum Capacity: 2
- Maximum Capacity: 4
- Subnets: private-subnet-az1 and private-subnet-az2
- ELB Health Check enabled
- Health Check Grace Period: 300 seconds
- Target Tracking Policy: Average CPU 50%

Security Groups:

ALB Security Group:
- Name: project3-q3-alb-sg
- HTTP 80 from 0.0.0.0/0

EC2 Security Group:
- Name: project3-q3-ec2-sg
- HTTP 80
- Outbound traffic allowed

Explain every AWS component in simple language:
1. VPC – why it is used
2. Availability Zones – why multiple AZs are used
3. Public Subnet – why ALB is placed here
4. Private Subnet – why application EC2 instances are placed here
5. Internet Gateway – its purpose
6. NAT Gateway – why private instances need it
7. Application Load Balancer – its purpose
8. Target Group – its purpose
9. Launch Template – its purpose
10. Auto Scaling Group – its purpose
11. Health Checks – why they are important
12. Security Groups – why they are required

Include these README sections:

# Project Title
# Project Overview
# Project Objective
# Architecture
# AWS Services Used
# Network Architecture
# VPC Configuration
# Subnet Configuration
# Route Tables
# Internet Gateway
# NAT Gateway
# Security Groups
# Launch Template
# Application Load Balancer
# Target Group
# Auto Scaling Group
# Health Checks
# User Data Script
# How Traffic Flows
# How Auto Scaling Works
# Testing
# Screenshots
# Project Status
# Challenges and Troubleshooting
# Key Learnings
# Interview Explanation
# Future Improvements
# Conclusion

Use professional but simple English suitable for a fresher/DevOps learner.

Do not claim the project is fully successful unless the ALB target health checks and application access are actually verified.

Also include a simple ASCII architecture diagram showing:

Internet
   |
Application Load Balancer
   |
+-----------------------------+
|          VPC                |
|                             |
| Public Subnets              |
|   ALB                       |
|                             |
| Private Subnet AZ1          |
|   EC2                       |
|                             |
| Private Subnet AZ2          |
|   EC2                       |
|                             |
| Auto Scaling Group          |
+-----------------------------+

Explain the complete architecture and traffic flow step by step.
