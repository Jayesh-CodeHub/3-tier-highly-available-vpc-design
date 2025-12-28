# 3-tier-highly-available-vpc-design

<img width="3998" height="1567" alt="image" src="https://github.com/user-attachments/assets/442c68e1-444f-4840-a1b9-cc90e2129c5e" />


This repository demonstrates a highly available three-tier VPC architecture designed on AWS.
The architecture follows best practices for security, scalability, and fault tolerance, using public and private subnets across multiple Availability Zones.

The design includes:

An Internet Gateway (IGW) attached to the VPC

NAT Gateways deployed in each Availability Zone

Separation of Web, Application, and Database tiers

This setup is commonly used in production-grade enterprise applications.

🧱 Architecture Description

The VPC is divided into three logical tiers:

1️⃣ Web Tier (Public Subnets)

Deployed in public subnets across multiple Availability Zones

Connected to the Internet Gateway

Hosts internet-facing resources such as:

Application Load Balancer (ALB)

Web servers (EC2 / ECS / EKS)

2️⃣ Application Tier (Private Subnets)

Deployed in private subnets

No direct internet access

Uses NAT Gateways for outbound internet connectivity (e.g., updates, package downloads)

Hosts backend services and APIs

3️⃣ Database Tier (Private Subnets)

Fully isolated private subnets

No internet access (neither IGW nor NAT)

Used for databases like:

RDS

Aurora

Self-managed databases on EC2

🌐 Network Components
Internet Gateway (IG)

Attached to the VPC

Enables internet access for resources in public subnets

NAT Gateways

One NAT Gateway per Availability Zone

Deployed inside public subnets

Ensures:

High availability

AZ-level fault isolation

Allows private subnet resources to access the internet securely

Availability Zones

Multiple AZs are used to:

Avoid single points of failure

Improve availability and resilience

Security Considerations

Public subnets only expose required endpoints

Private subnets have no direct internet access

NAT Gateways prevent inbound connections to private resources

Can be extended with:

Security Groups

NACLs

VPC Flow Logs
