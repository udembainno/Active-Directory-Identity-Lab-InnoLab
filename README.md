# Active Directory & Identity Lab (InnoLab)

## Overview
This project demonstrates the end-to-end deployment, configuration, and validation of an on-premises Active Directory environment. A Windows Server 2022 domain controller (DC1) and a Windows 11 client (CLIENT1) were configured to enforce authentication, authorization, and security policies using Active Directory Domain Services (AD DS), DNS, and Group Policy.


## Lab Environment
- Domain: innolab.local
- Domain Controller: DC1 (Windows Server 2022)
- Client: CLIENT1 (Windows 11 Pro)
- Networking:
  - Host-only adapter for AD/DNS communication
  - NAT Network adapter for internet access
- DC1 Host-only IP: 192.168.56.10/24
- DNS: 192.168.56.10 (AD-integrated)


## 1. Operating System Installation
- Installed Windows Server 2022 to serve as the domain controller foundation.
- Installed Windows 11 as a client system for domain join and policy validation.

Screenshots:
- `01-windows-server-installed.png`
- `02-windows-11-installed.png`


## 2. Network Configuration
- Configured DC1 with a static IP address and self-referencing DNS on the Host-only adapter to ensure reliable AD and DNS functionality.

Screenshot:
- `03-dc1-ip-dns.png`


## 3. Active Directory & DNS Deployment
- Installed Active Directory Domain Services (AD DS) and DNS Server roles.
- Promoted DC1 to a Domain Controller and created the `innolab.local` forest.
- Verified AD-integrated DNS forward lookup zones.

Screenshots:
- `04-ad-dns-installed.png`
- `05-domain-created-aduc.png`
- `06-dns-zone.png`


## 4. Active Directory Design
- Created a structured Organizational Unit (OU) hierarchy for scalable administration:
  - InnoLab → Users (HR, IT), Groups, Computers (Workstations, Servers)
- Created security groups and assigned users using role-based access control.

Screenshots:
- `07-ou-structure.png`
- `08-group-membership.png`


## 5. Group Policy Enforcement
- Configured domain-wide password complexity and account lockout policies via the Default Domain Policy.
- Applied a workstation security baseline GPO enforcing automatic session lock after inactivity.

Screenshots:
- `09-password-lockout-policy.png`
- `10-baseline-gpo.png`


## 6. Domain Join & Authentication Validation
- Successfully joined CLIENT1 to the `innolab.local` domain.
- Verified Group Policy application and authentication using `gpresult`.

Screenshots:
- `11-domain-join-success.png`
- `12-gpresult.png`


## 7. Authorization Validation (Access Control)
- Configured a secured HR network share on DC1.
- Verified access for authorized HR users.
- Confirmed access denial for non-HR users, enforcing least privilege.

Screenshots:
- `13-authz-granted.png`
- `14-authz-denied.png`


## Key Commands Used
- gpupdate /force
- gpresult /r
- ipconfig /all


