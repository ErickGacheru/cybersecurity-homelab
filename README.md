# 🛡 Enterprise Cybersecurity Home Lab (Hyper-V + Sophos)

## 📌 Project Summary

This project demonstrates the design, deployment, and troubleshooting of a virtual enterprise network security environment using Hyper-V and Sophos Firewall Home Edition.

The objective is to simulate a real-world corporate infrastructure for hands-on cybersecurity practice including network segmentation, firewall configuration, Active Directory integration, and attack detection.

This lab mirrors small-to-mid enterprise network architecture.


**Infrastructure Overview**

**Hypervisor:** Microsoft Hyper-V  
**Firewall:** Sophos Firewall Home Edition  
**Server OS:** Windows Server 2022 (Planned AD Deployment)  
**Network Model:** Segmented WAN / LAN architecture  

**Core Components**

- External Virtual Switch (WAN)
- Internal Virtual Switch (LAN)
- Sophos Firewall (Dual-homed)
- Internal Windows Server
- Future Domain-Joined Client Machines

---
## 📊 Network Diagram

![Enterprise Network Topology](diagrams/enterprise-network-topology.png)

**🔥 Firewall Deployment Details**

**Virtual Machine Configuration**

- Generation 1 (BIOS-based firmware)
- 4GB Static RAM (Dynamic memory disabled)
- 60GB Virtual Disk
- Dual Network Adapters:
  - Adapter 1 → vSwitch-LAN
  - Adapter 2 → vSwitch-WAN

**LAN Configuration**

- LAN IP: 172.16.16.16/24
- DHCP enabled for lab clients
- NAT routing enabled
- Secure Web Admin Access via HTTPS (Port 4444)

**Troubleshooting Performed**

This lab required diagnosing and resolving multiple deployment issues.

**PXE Boot Failure**
Issue:  
“The boot loader did not load an operating system.”

Root Cause:  
UEFI firmware incompatibility with Sophos image.

Resolution:  
Recreated VM using Generation 1 BIOS-based firmware.

---

**firstboot failed: swapon /dev/swap**

Root Cause:  
Dynamic memory instability and insufficient static allocation.

Resolution:  
Disabled Dynamic Memory and allocated fixed 4096MB RAM.

---

**No Web Interface Access**

Root Cause:  
Incorrect WAN/LAN interface mapping in Hyper-V.

Resolution:  
Corrected adapter assignments:
- LAN → Internal Switch
- WAN → External Switch

Successfully restored management access.

---

**Technical Skills Demonstrated**

- Virtualization deployment (Hyper-V)
- Network segmentation (Layer 3 design)
- Dual-homed firewall architecture
- NAT and gateway configuration
- Firewall web management configuration
- DHCP scope configuration
- Secure lab isolation principles

---

**Upcoming Enhancements**

- Deploy Windows Server 2022 Domain Controller
- Configure Active Directory & DNS
- Join Windows Client to domain
- Implement AD-based firewall policies
- Simulate attacker VM for detection testing
- Monitor traffic & security logs

---

## 🎯 Career Relevance

This project demonstrates hands-on capability with:

- Enterprise firewall deployment
- Network architecture design
- Infrastructure troubleshooting
- Practical cybersecurity lab simulation

The lab is continuously expanded to simulate real-world defensive security scenarios.

**Phase 2 – Active Directory Integration**

**Overview**

In this phase, the lab was expanded from a standalone firewall deployment to a fully functional enterprise domain environment.
A Windows Server 2022 Domain Controller was deployed and integrated with DNS to provide centralized identity and authentication services.
A Windows 11 Enterprise client was joined to the domain and authenticated using domain credentials.

**Infrastructure Components**

1. Firewall: Sophos Home Firewall (NAT Gateway)
2. Domain Controller: Windows Server 2022 (DC01)
3. Active Directory Domain Services
4. DNS Server
5. Client Machine: Windows 11 Enterprise (WIN11-CL01)
6. Internal Subnet: 172.16.16.0/24
7. Domain Name: corp.local

**Key Configuration Steps**

- Configured static IP addressing for domain infrastructure
- Deployed AD DS and DNS roles
- Created new forest: corp.local
- Created domain user account (labuser)
- Joined Windows 11 client to the domain
- Verified domain authentication and DNS resolution

📊 Updated Network Diagram

![Enterprise Network Topology](diagrams/enterprise-network-topology2.png)

🧠 Skills Demonstrated

**Active Directory deployment**
- DNS configuration and validation
- Static IP design and segmentation
- Domain user management
- Domain join troubleshooting
- Enterprise authentication workflow

🚀 Next Phase (Planned)

i. Group Policy deployment
ii. User-based firewall control
iii. Attack simulation using Kali Linux
iv. Logging and monitoring enhancements
