# ⚙️ Setup Guide

This document describes the setup of the **Secure Remote Access Infrastructure on AWS** using **VPC, EC2, and OpenVPN**.

---

## 1. VPC Setup
VPC CIDR: 10.0.0.0/16

Subnets:

| Subnet | CIDR | Purpose |
|------|------|------|
| Public Subnet | 10.0.1.0/24 | VPN Server |
| Private Subnet | 10.0.2.0/24 | Internal Server |

Internet Gateway attached to the VPC.
Route Table
Destination: 0.0.0.0/0
Target: Internet Gateway

---

## 2. Architecture
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

  
