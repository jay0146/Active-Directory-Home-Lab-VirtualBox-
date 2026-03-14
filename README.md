# Active Directory Home Lab (VirtualBox)

## Overview

This project demonstrates the setup of a basic **Active Directory environment** using **Oracle VirtualBox**.  
The lab simulates a small corporate network with a **Windows Server 2019 Domain Controller** and a **Windows 10 client machine** joined to the domain.

The goal of this project was to better understand how enterprise environments manage:

- centralized authentication
- user accounts
- computer management
- internal networking

This lab replicates a simplified version of a real office network.

---

## Technologies Used

- Windows Server 2019
- Windows 10
- Oracle VirtualBox
- Active Directory Domain Services
- DNS
- DHCP
- NAT / Routing
- PowerShell

---

## Lab Architecture

The environment consists of two virtual machines.

### Domain Controller (DC)

- Windows Server 2019
- Hosts **Active Directory Domain Services**
- Manages user accounts and authentication
- Runs **DNS and DHCP services**
- Provides NAT routing for internal clients
- Domain name: `mydomain.com`

### Client Machine (Client1)

- Windows 10
- Connected to the internal virtual network
- Receives network configuration through DHCP
- Joined to the Active Directory domain
- Authenticates using domain user accounts

---

## Network Configuration

The Domain Controller uses **two network adapters**.

Adapter 1  
Connected to **NAT** in VirtualBox to provide internet access.

Adapter 2  
Connected to a **VirtualBox internal network** to simulate a private company network.

The Windows 10 client connects to the **internal network** and communicates with the domain controller for authentication and network services.

---

## Network Diagram

The diagram below shows the architecture of the lab environment.  
The Domain Controller connects to the internet through a NAT adapter while also hosting an internal network for domain clients.

![Network Diagram](client 1 domain.png)

---

## Domain Authentication and Connectivity Test

The screenshot below shows a domain user successfully logged into the Windows 10 client machine.  
The command prompt verifies that the user is authenticated to the domain and that the machine has internet connectivity.

![Domain Authentication Test](vm.png)
