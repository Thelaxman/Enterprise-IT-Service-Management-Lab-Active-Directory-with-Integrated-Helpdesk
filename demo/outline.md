# Project Outline: Enterprise IT Service Management Lab

## Overview
This lab simulates a real-world enterprise IT environment with **Active Directory Domain Services (AD DS)** running on Windows Server 2022 and a **Windows 11 client** joined to the domain.  
The setup demonstrates networking, DHCP, NAT/RRAS, domain integration, and automated user provisioning.  

---

## Lab Environment
- **Hypervisor:** VMware Workstation  
- **Server:** Windows Server 2022  
  - Roles: AD DS, DHCP, NAT/RRAS  
  - Promoted as Domain Controller (`corp.local`)  
- **Client:** Windows 11 Enterprise  
- **Networking:** Dual NICs on Server  
  - External Adapter → Internet access  
  - Internal Adapter → Private network (`172.16.0.0/24`)  

---

## Network Configuration
- **Internal NIC (Server 2022):**  
  - IP: `172.16.0.1`  
  - Acts as **default gateway** for internal network  

- **DHCP Server Scope:**  
  - Range: `172.16.0.100 – 172.16.0.200`  
  - Provides automatic IPs to internal network clients  

- **NAT / RRAS:**  
  - Configured on Server 2022  
  - Allows internal clients to reach the internet through the external NIC  

---

## Active Directory Setup
1. Installed **Active Directory Domain Services (AD DS)** on Server 2022.  
2. Promoted the server to a **Domain Controller** for domain `mydomain.com`.  
3. Configured Organizational Units (OUs) and groups for structured management.  

---

## Automated User Provisioning
- Created a **PowerShell script** to automatically generate **1,000 domain users** with a default password.  
- Users stored in the `Users` OU for testing domain logins and ticketing workflows.  

---

## Client Configuration
1. Installed Windows 11 as a client VM.  
2. Changed hostname to align with domain naming standards.  
3. Joined the machine to the `corp.local` domain.  
4. Verified connectivity:  
   - Ping test to Domain Controller (`172.16.0.1`).  
   - Confirmed domain logon using provisioned user accounts.  

---

## Validation
- **DHCP:** Client successfully received IP from the `172.16.0.100–200` scope.  
- **Domain Join:** Client authenticated against AD DS.  
- **Connectivity:** Client able to ping Domain Controller and access internet via NAT.  
- **User Accounts:** 1,000 test accounts visible in Active Directory Users and Computers (ADUC).  

---

## Next Steps
- Integrate Peppermint Helpdesk with AD for centralized authentication.  
- Map AD groups to Peppermint roles for ITSM ticketing workflows.  
- Simulate end-to-end IT support scenarios (e.g., password reset requests).  
