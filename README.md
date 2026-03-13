# Active Directory Home Lab (VirtualBox)

## Overview

This project demonstrates the setup of a basic **Active Directory environment** using **Oracle VirtualBox**.  
The lab simulates a small corporate network with a **Windows Server 2019 Domain Controller** and a **Windows 10 client machine** joined to the domain.

The goal of this project was to better understand how enterprise environments manage:

- centralized authentication  
- user accounts  
- computer management  
- internal networking  

This lab replicates a simplified version of a real corporate network.

---

## Technologies Used

- Windows Server 2019  
- Windows 10  
- Oracle VirtualBox  
- Active Directory Domain Services (AD DS)  
- DNS  
- DHCP  
- NAT / Routing  
- PowerShell  

---

## Lab Architecture

The environment consists of **two virtual machines**.

### Domain Controller (DC)

- Windows Server 2019  
- Hosts **Active Directory Domain Services**
- Manages domain authentication and user accounts
- Runs **DNS and DHCP services**
- Provides NAT routing for internal clients
- Domain name: `mydomain.com`

### Client Machine (Client1)

- Windows 10
- Connected to the internal virtual network
- Receives network configuration automatically through DHCP
- Joined to the **Active Directory domain**
- Authenticates using domain user accounts

---

## Network Configuration

The Domain Controller uses **two network adapters**.

**Adapter 1 (External Network)**  
Connected to **NAT** in VirtualBox to provide internet access.

**Adapter 2 (Internal Network)**  
Connected to a **VirtualBox internal network** to simulate a private company network.

The Windows 10 client connects to the **internal network** and communicates with the Domain Controller for authentication, DNS resolution, and DHCP configuration.

---

## Client Joined to Domain

The Windows 10 client machine was successfully joined to the **mydomain.com Active Directory domain**.

The system information shows the fully qualified domain name (FQDN):

`CLIENT1.mydomain.com`

This confirms the machine is properly integrated into the domain environment and can authenticate domain users.

![Client Joined to Domain](client%201%20domain.PNG)

---

## Skills Demonstrated

- Active Directory Domain Services deployment
- Domain user and computer management
- Windows domain client configuration
- DHCP network configuration
- DNS integration with Active Directory
- Virtual network configuration using VirtualBox
- Basic enterprise network architecture concepts
