# Enterprise IT Service Management Lab: Active Directory with Integrated Helpdesk

## Project Overview
This lab simulates an enterprise IT environment where Active Directory (AD) is integrated with a ticketing system (Peppermint Helpdesk). It demonstrates a full IT support workflow, including user authentication, ticket management, and common administrative tasks, mimicking real-world enterprise operations.

## Components
- **Windows Server (AD DS)**  
  - Domain controller setup  
  - Organizational Units (OUs) and security groups  
  - User account creation  
- **Windows Clients**  
  - Joined to the AD domain  
  - Domain user logins for ticket submission  
- **Peppermint Helpdesk**  
  - Installed on Linux host or VM  
  - Integrated with Active Directory using LDAP authentication  
  - Role mapping: Users → End Users, Helpdesk → Technicians  

## Features
- **AD Integration:** Users log in to Peppermint with their domain credentials.  
- **Ticket Workflow:**  
  1. User raises a support ticket.  
  2. Technician resolves the issue using AD tools (e.g., password resets, account unlocks).  
  3. Ticket marked as resolved in Peppermint.  
- **Enterprise-style Role Management:** Permissions controlled via AD groups.  
- **End-to-End Demonstration:** Showcases IT support lifecycle in an enterprise environment.

## Project Goals
- Demonstrate understanding of Active Directory administration.  
- Showcase integration of ITSM tools with AD for enterprise workflows.  
- Simulate realistic IT support processes, including ticket handling and user management.

## Setup Instructions

### Windows Server (AD DS)
1. Install Windows Server 2019/2022 VM.  
2. Add the **Active Directory Domain Services** role.  
3. Create domain (e.g., `corp.local`), OUs, groups, and users.  
4. Configure Windows clients to join the domain.  

### Peppermint Helpdesk
1. Install LAMP/LEMP stack on Linux host.  
2. Install Peppermint Helpdesk.  
3. In Peppermint Admin → Authentication Settings → select **LDAP/Active Directory**.  
4. Configure:
   - LDAP Server: `ldap://<DomainController_IP>`  
   - Base DN: `DC=corp,DC=local`  
   - Bind DN: `<service_account>`  
   - Attribute mapping: username → `sAMAccountName`, email → `mail`, display name → `cn`  
5. Map AD groups to Peppermint roles:
   - `Helpdesk` → Technician/Agent  
   - `Users` → End Users  

### Demo Workflow
1. Domain user logs into Peppermint.  
2. User submits a ticket (e.g., password reset).  
3. Technician resolves the issue using AD tools.  
4. Technician marks ticket as resolved in Peppermint.  

## Technologies Used
- Windows Server 2019/2022  
- Windows 10/11 Clients  
- Peppermint Helpdesk  
- Linux Host (Ubuntu/Debian recommended)  
- LAMP/LEMP Stack (Apache/Nginx, PHP, MySQL/MariaDB)  
- LDAP/Active Directory integration  

## Learning Outcomes
- Hands-on experience with AD domain services and user/group management.  
- Practical understanding of integrating ITSM ticketing systems with enterprise authentication.  
- Demonstration of end-to-end IT support processes.  

## License
This project is for educational purposes.  
