# Simple Azure Home Lab

## Overview

This project documents the setup of a simple Azure home lab consisting of three virtual machines: a Windows 10 Pro (22H2), a Windows Server 2019 Datacenter, and Kali Linux 2023.4. The lab is designed for cybersecurity testing and experimentation, utilizing Azure's resources effectively while keeping costs minimal with a $200 credit.

## Table of Contents

1. [Home Lab Topology](#home-lab-topology)
   - [Steps to Create the Topology in Draw.io](#home-lab-topology)
2. [Lab Configuration](#lab-configuration)
   - [Virtual Machines](#virtual-machines)
   - [Inbound and Outbound Rules](#inbound-and-outbound-rules)
3. [Lab Setup Steps](#lab-setup-steps)
4. [Conclusion](#conclusion)

## Home Lab Topology

### Steps to Create the Topology in Draw.io

1. **Open Draw.io**:
   - Navigate to [Draw.io](https://www.draw.io) and create a new blank diagram.
   - [insert image]

2. **Add Virtual Machines**:
   - Drag and drop three rectangles onto the canvas, labeling them as **Windows 10 Pro (22H2)**, **Windows Server 2019 Datacenter**, and **Kali Linux (2023.4)**.
   - [insert image]

3. **Connect the VMs**:
   - Use the connector tool to draw lines between the Windows VMs and the Kali Linux VM, indicating their network relationships.
   - [insert image]

4. **Add Azure Internet Element**:
   - Include a cloud shape labeled **Azure Internet**, positioned below the VMs to represent external access.
   - [insert image]

5. **Label Connections**:
   - Use text boxes to indicate allowed protocols (RDP, SSH, HTTPS) for inbound connections, clearly marking the network topology.
   - [insert image]

## Lab Configuration

### Virtual Machines

1. **Windows 10 Pro (22H2) - x64 Gen2**: 
   - Ideal for testing client-side applications and understanding user-level security.

2. **Windows Server 2019 Datacenter - x64 Gen2**: 
   - Provides a server environment for learning about server management, Active Directory, and enterprise-level applications.

3. **Kali Linux 2023.4 - x64 Gen2**: 
   - A powerful tool for penetration testing and ethical hacking, allowing for hands-on experience with cybersecurity tools and techniques.

All virtual machines were created with the **Standard DC1s v3** size, featuring:
- **1 CPU**
- **Minimal resource allocation** to optimize usage of Azure credits.

### Inbound and Outbound Rules

- **Inbound Port Rules**:
  - **RDP (TCP 3389)**: Allowed for remote access to Windows machines.
  - **SSH (TCP 22)**: Enabled access to the Kali Linux machine.
  - **HTTPS (TCP 443)**: Configured for secure web traffic.

- **Outbound Rules**:
  - Allowed all outbound traffic to the internet over HTTPS.

## Lab Setup Steps

1. **Create Virtual Machines**:
   - Log into the Azure portal.
   - Create three virtual machines using the Gen2 option, selecting the appropriate OS images and sizes.
   - [insert image]

2. **Configure Network Security Groups (NSGs)**:
   - Set up inbound rules for RDP, SSH, and HTTPS.
   - Ensure that all outbound traffic is allowed for HTTPS.
   - [insert image]

3. **SSH into Kali Linux**:
   - Access the Kali Linux VM via SSH using the following command:
     ```bash
     ssh username@kali_ip_address
     ```
   - [insert image]

4. **Install and Configure XRDP on Kali Linux**:
   - Once logged into Kali, install XRDP to enable remote desktop access:
     ```bash
     sudo apt update
     sudo apt install xrdp
     ```
   - Start the XRDP service:
     ```bash
     sudo systemctl start xrdp
     sudo systemctl enable xrdp
     ```
   - Configure XRDP to allow access for the Windows 10 machine:
     ```bash
     echo "gnome-session" > ~/.xsession
     ```
   - [insert image]

5. **Connect to Kali Linux from Windows 10**:
   - Open Remote Desktop Connection on Windows 10.
   - Enter the IP address of the Kali Linux machine and connect.
   - Log in using your Kali credentials.
   - [insert image]

## Conclusion

This simple Azure home lab provides a versatile environment for cybersecurity testing, allowing hands-on experience with both Windows and Linux operating systems in a cloud setting. The Windows 10 Pro machine serves as a client-side testing environment, the Windows Server 2019 offers insights into enterprise-level server management, and the Kali Linux VM is a critical tool for penetration testing and ethical hacking. With minimal resources and costs, this lab is an excellent foundation for various projects and learning opportunities in a well-known enterprise cloud environment.

Feel free to explore, expand, and modify the lab for more advanced testing and development!
