# 🔐 Secure Remote Access Infrastructure on AWS

A secure remote access solution built on **AWS using OpenVPN** that allows users to access private infrastructure without exposing internal servers to the internet.

This project demonstrates **AWS VPC networking, VPN architecture, and secure infrastructure design**.

---

## 📌 Overview

Organizations often need remote access to internal systems.  
Exposing servers directly to the internet can lead to security risks such as:

- Unauthorized access
- Brute-force attacks
- Data breaches

This project solves the problem by implementing a **VPN gateway architecture** where users must connect through **OpenVPN** before accessing internal resources.

---

## 🏗 Architecture
            Internet
                │
                │
        ┌──────────────┐
        │  OpenVPN EC2 │
        │ PublicSubnet │
        └───────┬──────┘
                │
                │ VPN
                │
        ┌───────▼──────┐
        │ Private EC2  │
        │PrivateSubnet │
        └──────────────┘

---

## 🧰 Technologies

- AWS EC2
- AWS VPC
- OpenVPN
- Ubuntu Linux
- Networking (subnets, routing, security groups)

---

## 🔑 Key Features

- Secure VPN access
- Public & Private subnet architecture
- Private servers not exposed to internet
- SSH access only through VPN
- Network isolation inside VPC

---

## ⚙️ Workflow
    User
    │
    │ OpenVPN Connection
    ▼
    VPN Server
    │
    │ Internal Network
    ▼
    Private Server (SSH)

Example SSH access:
ssh ubuntu@private-ec2-ip

---

## 🧠 Skills Demonstrated

- AWS VPC networking
- VPN infrastructure design
- Linux server administration
- Secure cloud architecture
- SSH access control

---

## 🚀 Future Improvements

- Multi-factor authentication (MFA)
- Infrastructure as Code (Terraform)
- Centralized logging with CloudWatch
- High availability VPN setup
