# Azure Active Directory with On-Prem ADDS, DNS & DHCP Services
## Goals
- Configure Active directory, Domain Name Service, and Dynamic Host Control Protocol on a Windows server that is serving a client computer
- Configure Azure Active directory
- Synchronize the two active directory services, including creation, changing, and disabling of services
# Required Materials
- Server with Windows Server 2025 installed (or a virtual machine with Windows Server 2025) with administrative access
- Client computer (Windows 10 or 11, can also be a virtual machine) with administrative access
- Access to a Microsoft business premium account (There are student discount versions available, if you have access to these, that would be my recommendation)

## Step 1: Basic Setup
Network setup on ProxMox (The PfSense firewall on this network is not relevant to this lab, it can be ignored for these purposes)
- <img width="352" height="126" alt="image" src="https://github.com/user-attachments/assets/26ca415b-aa35-4db1-99bf-0f4cec2120e0" />
- Creation of a Windows 10 VM and a VM of Windows Server 2025

## Setup of On-Prem DHCP and DNS
- Go into Server Manager on the Windows Server 2025 machine
- Configure a static IP for the server (Recommendation: Use xxx.xxx.1.2, as 1.1 is reserved for your default gateway. This entire lab will be done using the 192.168 private address space, so my server will be 192.168.1.2)
-

