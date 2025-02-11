# Microsoft Azure Security Compliance Project

This project demonstrates the implementation of essential security and compliance configurations in Microsoft Azure, following best practices to enhance cloud security. Key components include creating Network Security Groups (NSGs) for traffic control, setting up compliance monitoring through Microsoft Defender for Cloud, and utilizing role-based access control (RBAC).

---

## Table of Contents

- [Project Overview](#project-overview)
- [Prerequisites](#prerequisites)
- [Setup Steps](#setup-steps)
  - [1. Resource Group Creation](#1-resource-group-creation)
  - [2. Configure Identity and Access Management (IAM) ](#2-configure-identity-and-access-management-IAM)
  - [3. Network Security Group (NSG) Configuration](#3-network-security-group-nsg-configuration)
  - [4. Associating NSG with a Subnet](#4-associating-nsg-with-a-subnet)
  - [5. Enabling Microsoft Defender for Cloud](#5-enabling-microsoft-defender-for-cloud)
  - [6. Reviewing Compliance Standards](#6-reviewing-compliance-standards)
- [Technologies Used](#technologies-used)
- [Limitations](#limitations)
- [Results](#results)
- [Screenshots](#screenshots)

---

## Project Overview

The goal of this project is to apply security best practices in Microsoft Azure to monitor and improve compliance. This includes configuring Network Security Groups to control network traffic, setting up role-based access control (RBAC), and monitoring compliance through Microsoft Defender for Cloud.

## Prerequisites

- An **Azure Free Subscription** (for basic setup) or **Azure Premium Trial** (for access to premium features like Azure AD Premium P1).
- Basic knowledge of Azure networking and security configurations.

## Setup Steps

### 1. Resource Group Creation

- **Purpose**: Create a resource group to organize all related resources in one manageable unit.
- **Steps**:
  - Go to **Azure Portal** > **Resource Groups** > **+ Create**.
  - Name the resource group `Azure-Security-Project`.
  - Select a region, review, and click **Create**.
- ![Resource Group Creation](Screenshots/resource-group-creation.png)

### 2. Configure Identity and Access Management (IAM)
- Set up role-based access control (RBAC) by assigning the **Owner** and **Contributor** roles.
- ![IAM Role Setup](Screenshots/IAM-Role-Assigning.png)

### 3. Network Security Group (NSG) Configuration

**Purpose**: Control inbound and outbound traffic to secure Azure resources.

#### a. Creating the NSG

- **Steps**:
  - In **Azure Portal**, go to **Network Security Groups** and select **+ Create**.
  - Name the NSG `Project-NSG` and assign it to `Azure-Security-Project`.
  - Click **Review + Create**, then **Create**.
- ![NSG Creation](Screenshots/nsg-creation.png)

#### b. Configuring Inbound Security Rules

1. **Allow SSH (Port 22)**:
   - Allows SSH access for management purposes.
   - Set **Source**: Any, **Destination Port**: 22, **Protocol**: TCP, **Action**: Allow.
   - ![Allow SSH](Screenshots/nsg-inbound-allow-ssh.png)

2. **Allow HTTP (Port 80)**:
   - Allows web access over HTTP.
   - Set **Source**: Any, **Destination Port**: 80, **Protocol**: TCP, **Action**: Allow.
   - ![Allow HTTP](Screenshots/nsg-inbound-allow-http.png)

3. **Deny All Inbound**:
   - A catch-all rule to block other inbound traffic.
   - Set **Source** and **Destination Port**: Any, **Protocol**: Any, **Action**: Deny.
   - ![Deny All Inbound](Screenshots/nsg-inbound-deny-all.png)

#### c. Configuring Outbound Security Rules

1. **Allow HTTP/HTTPS (Ports 80, 443)**:
   - Allows outbound traffic over HTTP/HTTPS.
   - Set **Destination Port Range**: 80, 443.
   - ![Allow HTTP/HTTPS Outbound](Screenshots/nsg-outbound-allow-http-https.png)

2. **Deny All Outbound**:
   - Blocks all other outbound traffic.
   - Set **Destination Port Range**: 0-65535.
   - ![Deny All Outbound](Screenshots/nsg-outbound-deny-all.png)

### 4. Associating NSG with a Subnet

- **Purpose**: Apply NSG rules to resources within a subnet.
- **Steps**:
  - Go to **Settings** > **Subnets** in the NSG.
  - Select the virtual network and subnet (e.g., `Project-VNet` and `Project-Subnet`).
  - Click **OK** to associate.
- ![NSG Subnet Association](Screenshots/nsg-subnet-association.png)

### 5. Enabling Microsoft Defender for Cloud

- **Purpose**: Activate compliance and threat protection features.
- **Steps**:
  - Go to **Microsoft Defender for Cloud** in Azure Portal.
  - Select **Upgrade** to activate Defender features, or start a free trial if needed.
  - Enable relevant **Defender for Cloud plans**.
- ![Defender Settings](Screenshots/defender-settings.png)

### 6. Reviewing Compliance Standards

- **Purpose**: Review the environment's compliance with standards like **NIST** and **CIS**.
- **Steps**:
  - In **Microsoft Defender for Cloud**, go to **Regulatory Compliance**.
  - Select a standard (e.g., **NIST SP 800-53**) to view compliance status.
- ![Compliance Dashboard](Screenshots/compliance-dashboard.png)

## Technologies Used

- **Microsoft Azure** - Cloud computing platform.
- **Microsoft Defender for Cloud** - Compliance and threat protection.
- **Network Security Groups (NSG)** - Network access control.
- **Azure Active Directory** - Identity and access management.

## Limitations

Due to the **standard subscription**, some advanced compliance and MFA settings were unavailable. Access to full regulatory compliance features requires **Azure AD Premium P1 or P2**.

## Results

This project demonstrates how to set up basic security controls and compliance monitoring in Microsoft Azure. It includes traffic control with NSGs, basic RBAC setup, and Microsoft Defender for Cloud compliance monitoring.

## Screenshots

Below are links to key screenshots used throughout the project:

- [Resource Group Creation](Screenshots/resource-group-creation.png)
- [NSG Creation](Screenshots/nsg-creation.png)
- [Allow SSH Inbound Rule](Screenshots/nsg-inbound-allow-ssh.png)
- [Allow HTTP Inbound Rule](Screenshots/nsg-inbound-allow-http.png)
- [Deny All Inbound Rule](Screenshots/nsg-inbound-deny-all.png)
- [Allow HTTP/HTTPS Outbound Rule](Screenshots/nsg-outbound-allow-http-https.png)
- [Deny All Outbound Rule](Screenshots/nsg-outbound-deny-all.png)
- [NSG Subnet Association](Screenshots/nsg-subnet-association.png)
- [Defender Settings](Screenshots/defender-settings.png)
- [Compliance Dashboard](Screenshots/compliance-dashboard.png)
