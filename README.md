# AWS VPC Peering – Internship Project

<p align="center">
  <strong>Cloud Computing | AWS Networking | Cloud Security</strong>
</p>

## 📌 Project Overview

This project demonstrates private communication between two Amazon Virtual Private Clouds (VPCs) using AWS VPC Peering.

The lab was implemented using Amazon EC2 instances, public and private subnets, route tables, security groups, and a bastion host. Connectivity and security controls were tested to understand how resources communicate securely across VPCs.

## 🎯 Project Objectives

* Create two separate VPCs with non-overlapping CIDR ranges.
* Configure public and private subnets.
* Establish a VPC Peering connection.
* Configure route tables for inter-VPC communication.
* Deploy a bastion host and two private EC2 instances.
* Configure security groups to control network traffic.
* Test connectivity in both directions.
* Perform controlled failure and recovery testing.

## 🏗️ AWS Architecture

The lab contains two VPCs connected through a VPC Peering connection.

| Resource               | Name            | CIDR / Private IP     |
| ---------------------- | --------------- | --------------------- |
| VPC A                  | `ewb-vpc-a`     | `10.10.0.0/16`        |
| VPC B                  | `ewb-vpc-b`     | `10.20.0.0/16`        |
| Public subnet          | `ewb-a-public`  | `10.10.1.0/24`        |
| Private subnet A       | `ewb-a-private` | `10.10.2.0/24`        |
| Private subnet B       | `ewb-b-private` | `10.20.1.0/24`        |
| Bastion host           | `ewb-bastion`   | `10.10.1.10`          |
| Application instance A | `ewb-app-a`     | `10.10.2.10`          |
| Application instance B | `ewb-app-b`     | `10.20.1.10`          |
| VPC Peering            | `ewb-a-b-peer`  | Active during testing |

**AWS Region:** Asia Pacific (Mumbai) — `ap-south-1`

## 🛠️ AWS Services and Technologies

* Amazon Virtual Private Cloud (VPC)
* Amazon EC2
* VPC Peering
* Public and private subnets
* Route tables
* Internet Gateway
* Security groups
* Amazon Linux 2023
* SSH and ICMP Ping

## 🔐 Security Implementation

* Used a bastion host to access private EC2 instances.
* Restricted SSH access through security-group source rules.
* Used private IP addresses for inter-VPC communication.
* Configured route tables to direct traffic through the VPC Peering connection.
* Tested how security-group rules affect network connectivity.

## 🧪 Testing and Results

The following tests were performed during the lab:

| Test                                           | Result   |
| ---------------------------------------------- | -------- |
| App-A → App-B connectivity                     | ✅ Passed |
| App-B → App-A connectivity                     | ✅ Passed |
| Controlled ICMP blocking                       | ✅ Passed |
| Connectivity recovery after restoring the rule | ✅ Passed |

### Test Summary

**Successful connectivity:** Both application instances exchanged ICMP packets through the VPC Peering connection, with four packets received and zero packet loss in each direction.

**Controlled failure:** Temporarily removing the ICMP inbound rule for App-B caused the ping from App-A to fail, with 100% packet loss.

**Recovery:** After restoring the ICMP rule, connectivity was verified again successfully.

## 📄 Project Report

The detailed project report contains AWS console screenshots and terminal evidence of the configuration and connectivity tests.

**Report file:** `AWS_VPC_Peering_Internship_Report.pdf`

Open the PDF file in this repository to review the implementation evidence.

## 📚 Key Learnings

* VPC and subnet design
* CIDR addressing
* VPC Peering configuration
* Route-table configuration
* EC2 deployment and SSH access
* Security-group configuration
* Private network troubleshooting
* Connectivity validation and failure recovery
* Basic cloud network security concepts

## 🧹 Resource Cleanup

The three EC2 instances were terminated after testing.

Other AWS resources should be checked separately and removed when no longer needed to help avoid unnecessary charges.

## 🎓 Project Purpose

This project was completed as part of an internship learning exercise focused on AWS networking, cloud infrastructure, and security fundamentals.

---

**Note:** This repository is for educational and internship purposes. It does not require AWS credentials or private SSH keys.
