# Incident Report: Internal Network Reconnaissance Using Nmap

## Overview

This lab simulates an attacker performing internal network reconnaissance against a Windows workstation inside a flat virtual network environment. The objective was to identify active hosts, enumerate open services, gather system information, and understand how exposed services could be leveraged in later attack phases.

---

## Lab Environment

| Machine           | Role            | IP Address      |
| ----------------- | --------------- | --------------- |
| Kali Linux        | Attacker        | 192.168.120.100 |
| Windows 10        | Victim          | 192.168.120.110 |
| Wazuh             | SIEM/Monitoring | 192.168.120.107 |
| Ubuntu Production | Server          | 192.168.120.120 |

---

## Tools Used

* Nmap
* Kali Linux
* Windows 10
* VirtualBox

---

## Commands Executed

### Host Discovery

```bash
nmap -sn 192.168.120.0/24
```

Purpose:

* Identify live hosts on the network
* Confirm target availability

---

### Service Enumeration

```bash
nmap -sV 192.168.120.110
```

Purpose:

* Identify running services
* Detect service versions

---

### Aggressive Enumeration

```bash
nmap -A 192.168.120.110
```

Purpose:

* Detect operating system
* Gather additional host information
* Discover SMB and NetBIOS details

---

## Findings

Open services discovered:

| Port | Service | Description                        |
| ---- | ------- | ---------------------------------- |
| 135  | MSRPC   | Microsoft Remote Procedure Call    |
| 139  | NetBIOS | Windows session service            |
| 445  | SMB     | File sharing and authentication    |
| 5357 | HTTPAPI | Microsoft device discovery service |

Additional information collected:

* Operating System: Windows 10
* Hostname: WINDOWSGUEST
* SMB signing enabled but not required
* Network distance: 1 hop

---

## Security Analysis

The scan identified SMB exposure on TCP port 445. SMB is commonly targeted because it may allow:

* Username enumeration
* Shared folder access
* Password attacks
* Credential abuse
* Lateral movement opportunities

NetBIOS exposure may reveal additional system information that could assist an attacker during future stages of reconnaissance.

---

## Screenshots

### Host Discovery Output

![Host Discovery](../screenshots/host-discovery.png)

### Service Enumeration

![Service Enumeration](../screenshots/service-enumeration.png)

### Aggressive Enumeration

![Aggressive Enumeration](../screenshots/aggressive-enumeration.png)

---

## Lessons Learned

* Reconnaissance is the first stage of many attacks.
* Open ports reveal potential attack surfaces.
* SMB services should be monitored and secured.
* Enumeration provides valuable information before exploitation begins.
* Nmap can identify operating systems, services, and host information with minimal interaction.

---

## Next Steps

The next phase of this project will include:

* SMB enumeration
* Shared folder discovery
* Weak password testing
* Hydra credential attacks
* Detection and monitoring through Wazuh

