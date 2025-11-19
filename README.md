# aws-cross-region-vpc-peering

# Cross-Region VPC Peering Setup

## 📝 Project Summary (Human‑Style)

This project is a practical, hands-on implementation of **cross-region VPC peering** between two AWS regions — **Singapore** and **Ireland**. I created two separate VPCs with their own subnets, route tables, and internet gateways. After setting up the network environments in both regions, I initiated a peering request from the Singapore VPC to the Ireland VPC and accepted it from the other side.

Once the peering connection was established, I updated the route tables in both VPCs to allow private traffic to flow between them. Then, I launched EC2 instances inside each subnet and tested connectivity using their **private IP addresses**. Successful ping responses confirmed that both instances could communicate securely across regions without using the public internet.

This project helped me clearly understand AWS networking concepts such as **CIDR planning, route propagation, security group rules, and inter-region communication**, making it a strong foundational networking exercise.

A simple, clean, and beginner‑friendly documentation of setting up **Cross‑Region VPC Peering** between two VPCs in different AWS regions. This project demonstrates how to enable secure private communication between EC2 instances across regions using VPC peering.

---

## 🚀 Project Overview

This project sets up:

* **Two VPCs in different AWS regions**
* **Subnets** inside each VPC
* **EC2 instances** for testing connectivity
* A **VPC Peering Connection** to allow private traffic between VPCs
* Updated **Route Tables** and **Security Group Rules** to enable ping/SSH

This setup helps understand real‑world multi‑region architecture and cross‑region networking on AWS.

---

## 🗺️ Architecture

### **Region A – Asia Pacific (Singapore) (ap-southeast-1)

* **VPC-A:** `10.0.0.0/16`
* **Subnet-A:** `10.0.0.0/17`
* **EC2-A:** Private IP `10.0.63.38`

### **Region B – Europe (Ireland) (eu-west-1)**

* **VPC-B:** `172.16.0.0/16`
* **Subnet-B:** `172.16.0.0/17`
* **EC2-B:** Private IP `172.16.88.161`:** Private IP `172.16.1.20`

A **VPC Peering Connection** is created between **VPC-A ↔ VPC-B**, allowing both EC2 instances to communicate privately.

---

## 🧰 Prerequisites

Before starting, ensure you have:

* An **AWS account**
* Permission to create VPCs, EC2, and networking components
* Basic understanding of AWS console navigation
* SSH key pair for EC2 access

---

## 🛠️ Setup Steps (Short Version)

### **1. Create VPCs**

* VPC-A in ap-south-1 → `10.0.0.0/16`
* VPC-B in us-east-1 → `172.16.0.0/16`

### **2. Create Subnets**

* Subnet-A → `10.0.1.0/24`
* Subnet-B → `172.16.1.0/24`

### **3. Launch EC2 instances**

* EC2-A in Subnet-A → private IP `10.0.1.10`
* EC2-B in Subnet-B → private IP `172.16.1.20`

### **4. Create VPC Peering Connection**

* Requester: VPC-A
* Accepter: VPC-B
* Accept the peering connection from VPC-B side

### **5. Update Route Tables**

* VPC-A RT → add route `172.16.0.0/16 → pcx-xxxx`
* VPC-B RT → add route `10.0.0.0/16 → pcx-xxxx`

### **6. Update Security Groups**

Allow ICMP/SSH **from the peer VPC CIDR**.

* On EC2-A SG → allow from `172.16.0.0/16`
* On EC2-B SG → allow from `10.0.0.0/16`

### **7. Test Connectivity**

SSH into EC2-A and run:

```
ping 172.16.1.20
```

SSH into EC2-B and run:

```
ping 10.0.1.10
```

If peering and routes are correct, the ping will succeed.

---

## 📦 Repository Contains

* `README.md` — High-level explanation (this file)
* `docs/` — Full step-by-step explanation with snapshot placeholders (optional)
* Architecture diagram

---

## 🎯 Learning Outcomes

By completing this project, you will understand:

* How VPC routing works
* Cross‑region VPC Peering architecture
* How security groups and routes enable communication
* How EC2 instances communicate privately across regions

---

## 📘 License

This repository is for educational purposes. Feel free to fork, modify, and reuse.

---

## 🙋 Need the full documentation file?

I can generate:
✔ Full step‑by‑step documentation
✔ With snapshot sections
✔ With diagram included

Just tell me: **“Generate full documentation.”**

