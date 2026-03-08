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

---

## 3. EC2 Instances

### VPN Server

OS: Ubuntu 22.04

Subnet: Public

Public IP: Enabled

Software: OpenVPN

### Internal Server
OS: Ubuntu 22.04

Subnet: Private

Public IP: Disabled

---

## 4. Security Groups

### VPN Server

| Port | Protocol | Source |
|-----|-----|-----|
| 22 | TCP | Admin IP |
| 1194 | UDP | Anywhere |

### Internal Server

| Port | Protocol | Source |
|-----|-----|-----|
| 22 | TCP | VPC CIDR |
| ICMP | - | VPC CIDR |

---

## 5. Access Flow
---
            User
            │
            │ OpenVPN Connection
            ▼
            VPN Server
            │
            │ Internal Network
            ▼
            Private Server (SSH)
---

Users connect to **OpenVPN** and then access the **private EC2 server via SSH**.

  
