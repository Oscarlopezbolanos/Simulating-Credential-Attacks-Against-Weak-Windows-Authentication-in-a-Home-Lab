# Simulating-Credential-Attacks-Against-Weak-Windows-Authentication-in-a-Home-Lab

##Project Overview
--
This project simulates common credential attacks against a vulnerable Windows environment within a controlled home lab. The purpose was to understand how attackers enumerate systems, discover weak authentication practices, gain access through password attacks, and how defenders can detect and mitigate those activities using Wazuh SIEM and network hardening techniques.

The project was initially deployed on a flat network to intentionally increase exposure between systems and demonstrate the risks of poor segmentation. Later phases introduced security controls including stronger authentication, account lockout policies, and pfSense-based network segmentation.
Objectives
Practice host discovery and service enumeration
Simulate SMB and RDP credential attacks
Analyze attack logs using Wazuh
Investigate Windows Event IDs
Understand lateral movement concepts
Implement security hardening techniques
Compare flat versus segmented network architectures
Lab Environment
Initial Flat Network Configuration
Machine
IP Address
Role
Kali Linux
192.168.120.106
Attacker
Wazuh Server
192.168.120.107
SIEM
Ubuntu Production
192.168.120.120
Linux Server
Windows 11 Pro
192.168.120.110
Victim
Initial Environment Issue
After transitioning the lab to a flat network architecture, all virtual machines lost their IP addresses and were unable to communicate across the network.
Symptoms
Machines failed to obtain DHCP addresses
Connectivity between systems was lost
Network discovery scans returned no results
Resolution
Static IP addresses were manually assigned to each virtual machine:
Kali: 192.168.120.106
Wazuh: 192.168.120.107
Ubuntu Production: 192.168.120.120
Windows: 192.168.120.110
Lesson Learned
Flat network changes can affect DHCP behavior and virtual network adapters in VirtualBox. Understanding static addressing and network configuration is critical during troubleshooting.
Windows Configuration
User Accounts Created
User
Password
Purpose
accounting
Summer2025
Weak password
manager
Password123
Weak password
intern
intern
Very weak password
admin.local
Admin123!
Privileged account
backupsvc
Backup2025
Service account
Security questions for all users:
Plain text
sysco
Intentional Misconfigurations
The Windows system was intentionally configured with insecure settings to simulate real-world weaknesses:
Enabled:
SMB File Sharing
Public share
Finance share
Remote Desktop Protocol (RDP)
Sample files added:
Plain text
payroll.xlsx
passwords.txt
clients.docx
Security controls intentionally weakened:
Weak passwords
No account lockout policy
Relaxed firewall configuration
SMB enabled
Note: These configurations were used only within the isolated lab environment.
