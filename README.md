# 🔐 Zero Trust University Network

[![FortiGate](https://img.shields.io/badge/Firewall-FortiGate-red)](https://www.fortinet.com/)
[![Proxmox](https://img.shields.io/badge/Virtualization-Proxmox%20VE-orange)](https://www.proxmox.com/)
[![Kali Linux](https://img.shields.io/badge/Pentesting-Kali%20Linux-blue)](https://www.kali.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

A practical cybersecurity project focused on designing and deploying a **Zero Trust architecture** for securing a university network using **FortiGate**, **Proxmox VE**, **VLAN segmentation**, and **penetration testing**.

> *"Never trust, always verify."*

---

## 📖 Project Overview

This project was carried out as part of my Bachelor's degree in **Network and Telecommunications Engineering** at **École Supérieure Polytechnique (ESP), Cheikh Anta Diop University, Dakar**.

The objective was to design a secure university network based on the **Zero Trust** model, ensuring that no user or device is trusted by default. The infrastructure was deployed in a virtual environment using **Proxmox VE**, while **FortiGate** was configured as the central security gateway.

---

## 🏗 Architecture

![Zero Trust Architecture](https://raw.githubusercontent.com/sokhnamaimounacisse-tech/zero-trust-university-network/main/architecture/zero-trust-architecture.png.jpeg)

The network is divided into five isolated VLANs:

| VLAN | Role | Subnet |
|------|------|--------|
| VLAN 10 | Administration | 192.168.10.0/24 |
| VLAN 20 | Teachers | 192.168.20.0/24 |
| VLAN 30 | Students | 192.168.30.0/24 |
| VLAN 40 | Servers | 192.168.40.0/24 |
| VLAN 50 | IoT Devices | 192.168.50.0/24 |

All traffic between VLANs is inspected by FortiGate according to the **Least Privilege** principle. Inter-VLAN traffic is **denied by default** unless explicitly authorized.

---

## 🛠 Technologies Used

- **FortiGate** (FortiOS 7.x) — Next-Generation Firewall
- **Proxmox VE** — Virtualization platform
- **Ubiquiti UniFi** — Network access layer (simulated via Proxmox bridges)
- **Debian 13** — Client VMs
- **Kali Linux 2026.1** — Penetration testing
- VLAN (802.1Q), DHCP, NAT

### Security Tools
- Nmap
- Hydra
- hping3
- arpspoof / dsniff

---

## 🔒 Security Policies

✔ Default Deny  
✔ Least Privilege  
✔ Inter-VLAN Isolation  
✔ Controlled Internet Access  
✔ Network Segmentation

![Firewall Policies](https://raw.githubusercontent.com/sokhnamaimounacisse-tech/zero-trust-university-network/main/screenshots/firewall-policy.png)

---

## 🧪 Penetration Tests

Five categories of security assessments were performed from a Kali Linux VM positioned in the Students VLAN, simulating an internal threat (a compromised student workstation):

1. **Vulnerability Scan** (Nmap)
2. **SSH Brute Force** (Hydra)
3. **Aggressive Scan & IPS Detection** (Nmap)
4. **SYN Flood DoS Attack** (hping3)
5. **ARP Spoofing** (arpspoof)

![Aggressive Nmap Scan](https://raw.githubusercontent.com/sokhnamaimounacisse-tech/zero-trust-university-network/main/screenshots/scan-agressif-nmap-ips.png)

![ARP Spoofing Attack](https://raw.githubusercontent.com/sokhnamaimounacisse-tech/zero-trust-university-network/main/screenshots/arp-spoofing.png)

---

## 📊 Results

| Test | Result | Security Level |
|------|--------|-----------------|
| Vulnerability Scan | No critical vulnerability | High |
| Inter-VLAN Isolation | No host detected outside VLAN 30 | High |
| SSH Brute Force | Blocked by FortiGate | High |
| Aggressive Scan / IPS | Detected (99% CPU spike) | Good |
| DoS Attack | 98,279 packets blocked | High |
| ARP Spoofing | Vulnerability detected (DAI absent) | Medium |

The project successfully demonstrated secure VLAN isolation, controlled inter-segment access, and protection against lateral movement and DoS attacks — while identifying a residual ARP Spoofing vulnerability due to the absence of Dynamic ARP Inspection.

---

## 🚀 Future Improvements

- Dynamic ARP Inspection (DAI)
- Multi-Factor Authentication (MFA)
- SIEM integration & centralized monitoring
- IPS signature enhancement (FortiGuard)
- Network Access Control (NAC)
- ISO 27001 certification pathway

---

## 📁 Repository Structure
