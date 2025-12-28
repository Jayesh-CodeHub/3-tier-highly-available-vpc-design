---

# 🏗️ Three-Tier VPC Architecture on AWS

## 📌 Overview

This repository demonstrates a **highly available three-tier VPC architecture** on AWS, designed using industry best practices for **security, scalability, and fault tolerance**.

The architecture uses **multiple Availability Zones**, separates **public and private subnets**, and is suitable for **production-grade enterprise workloads**.

---

## 🧱 Architecture Design

The system follows a **three-tier network architecture**:

* The **VPC** is connected to the internet using an **Internet Gateway (IG)**
* **Public subnets** are created in each Availability Zone
* A **NAT Gateway is deployed in each public subnet (one per AZ)** for high availability
* **Private subnets** host the application and database tiers with no direct internet exposure

---

## 🖼️ Architecture Diagram

<img width="3998" height="1567" alt="Three Tier VPC Architecture Diagram" src="https://github.com/user-attachments/assets/442c68e1-444f-4840-a1b9-cc90e2129c5e" />

---

## 🧩 Tier Breakdown

### 1️⃣ Web Tier (Public Subnets)

* Deployed in **public subnets across multiple Availability Zones**
* Has a route to the **Internet Gateway**
* Hosts:

  * Application Load Balancer (ALB)
  * Web servers (EC2 / ECS / EKS)
* Accepts inbound internet traffic

---

### 2️⃣ Application Tier (Private Subnets)

* Deployed in **private subnets**
* No direct internet access
* Outbound internet access via **NAT Gateway**
* Hosts:

  * Backend services
  * APIs
  * Application logic

---

### 3️⃣ Database Tier (Private Subnets)

* Fully isolated **private subnets**
* No access to Internet Gateway or NAT Gateway
* Hosts:

  * Amazon RDS
  * Aurora
  * Self-managed databases

---

## 🌐 Core Network Components

### Internet Gateway (IG)

* Attached to the VPC
* Enables inbound and outbound internet connectivity for **public subnets**

### NAT Gateway

* Deployed **one per Availability Zone**
* Placed inside **public subnets**
* Allows instances in private subnets to:

  * Download updates
  * Access external APIs
* Prevents inbound internet traffic to private resources

### Availability Zones

* Multiple AZs are used to:

  * Eliminate single points of failure
  * Increase fault tolerance
  * Improve availability

---

## 🔁 Traffic Flow

### Inbound Traffic

Internet → Internet Gateway → Public Subnet (Web Tier)

### Outbound Traffic (Private Subnets)

Private Subnet → NAT Gateway → Internet Gateway → Internet

### Internal Communication

Web Tier → Application Tier → Database Tier

---

## 🔐 Security Best Practices

* Public access limited to **Web Tier only**
* Application and Database tiers are **not internet-facing**
* NAT Gateways prevent inbound access to private subnets
* Can be enhanced using:

  * Security Groups
  * Network ACLs
  * VPC Flow Logs
  * IAM Roles

---

## 🧠 Key Terminology

| Component         | Description                                           |
| ----------------- | ----------------------------------------------------- |
| VPC               | Isolated virtual network in AWS                       |
| Internet Gateway  | Connects the VPC to the internet                      |
| NAT Gateway       | Enables outbound internet access from private subnets |
| Availability Zone | Isolated data center within a region                  |
| Public Subnet     | Subnet with a route to the Internet Gateway           |
| Private Subnet    | Subnet without direct internet access                 |

---

## 🚀 Why This Architecture?

* High Availability
* Secure by Design
* Fault Tolerant
* Scalable
* Production Ready
* Interview Standard Architecture

---

## 📚 Use Cases

* Enterprise web applications
* Microservices-based systems
* Secure backend platforms
* Cloud & DevOps interview demonstrations

---

## 🛠️ Future Enhancements

* Terraform / CloudFormation implementation
* Auto Scaling Groups
* Bastion Host or AWS SSM Session Manager
* VPC Endpoints (S3, DynamoDB)
* AWS WAF & Shield integration

---

## 📎 Author

**Jayesh Tripathi**
DevOps Engineer | Cloud & Kubernetes Enthusiast

---



