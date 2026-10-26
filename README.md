# 🔐 Cybersecurity & Penetration Testing Lab Setup (Dual OS)

**Author:** Mohamed Sufiyan Afham  
**Program:** Cybersecurity Training – Networkwalks (Batch B084)  
**Instructor:** Sir Waqas Karim (CCIE)  
**Lab Environment:** Oracle VM VirtualBox (v7.x)

---

## 📌 Overview

This project documents the installation, configuration, and verification of an isolated, multi-OS virtualization lab designed for practical cybersecurity and penetration testing workflows. 

The lab hosts both **Kali Linux** and **Windows 10** inside an isolated private **NAT Network**, establishing secure inter-VM communication while preserving outbound Internet routing for updates and package management.

---

## 🏗️ Architecture & Topology

```text
               +-----------------------------------+
               |       Host Machine (Hypervisor)   |
               |         Oracle VM VirtualBox      |
               +-----------------+-----------------+
                                 |
                 +---------------+---------------+
                 |  VirtualBox NAT Network       |
                 |  Subnet: 10.0.2.0/24 (DHCP)   |
                 +-------+---------------+-------+
                         |               |
                         |               |
         +---------------+--+         +--+---------------+
         |   Kali Linux     | <-----> |   Windows 10     |
         |   IP: 10.0.0.2  |  ICMP   |   IP: 10.0.0.10  |
         +------------------+  Pings  +------------------+


## ⚙️ Step-by-Step Implementation

### 1. Hypervisor & Network Provisioning
1. Installed **Oracle VM VirtualBox** along with the **VirtualBox Extension Pack**.
2. Created a dedicated NAT Network via **Tools ➔ Network Manager ➔ NAT Networks**:
   - **Network Name:** `CyberLabNet`
   - **IPv4 Prefix:** `10.0.2.0/24`
   - **DHCP:** Enabled

### 2. Kali Linux VM Configuration
1. Imported/installed the official Kali Linux VirtualBox appliance.
2. Under **Settings ➔ Network ➔ Adapter 1**:
   - Attached to: **NAT Network**
   - Name: `CyberLabNet`
   - Promiscuous Mode: `Allow All` (or default)
3. Booted the VM and retrieved IP details:
   ```bash
   ip a

1. Tested local resolution and default gateway routing:
Bash
ping -c 4 8.8.8.8

2. Windows 10 VM Configuration (Bonus Project)
1.Deployed a clean Windows 10 virtual machine.
2.Configured VM network settings under Settings ➔ Network ➔ Adapter 1:
• Attached to: NAT Network
• Name: CyberLabNet

3. Verified adapter configuration via Command Prompt:
DOS
ipconfig /all

4. Enabled inbound ICMP requests through Windows Defender Firewall to permit ping replies from Kali:
DOS
netsh advfirewall firewall add rule name="Allow ICMPv4-In" protocol=icmpv4:any,any dir=in action=allow

🧪 Verification & Connectivity Testing
1. Bidirectional Ping Verification
To prove intra-network routing and full bidirectional reachability, ping tests were executed between both endpoints:

○ Windows 10 ➔ Kali Linux:
DOS
ping <Kali_IP_Address>
○ Kali Linux ➔ Windows 10:
Bash
ping -c 4 <Windows_IP_Address>
Result: 0% packet loss in both directions.

2. State Snapshot Creation
To safeguard against misconfigurations, malware execution, or breaking changes during future lab tasks, baseline snapshots were generated immediately post-verification:
•Kali-Clean-Base-State
•Win10-Clean-Base-State

📸 Screenshots & Evidence
1. VirtualBox NAT Network Configuration
2. Bidirectional Connectivity (Dual Ping Proof)
Screenshot displaying both terminal windows side-by-side with successful ping output:

3. VM Snapshots
🎯 Key Learnings
○ NAT vs. NAT Network: Traditional NAT only enables outbound guest communication to the external network, whereas a private NAT Network enables inter-VM routing on a shared virtual segment.

○ Firewall Filtering: Windows blocks inbound ICMP (Echo Request) packets by default; configuring explicit firewall rules is required for inter-VM discovery.

○ Snapshot Hygiene: Generating a clean baseline before testing guarantees frictionless recovery without redeploying the base operating systems.


👏 Acknowledgments
Special thanks to Sir @Waqas Karim (CCIE) and the @Networkwalks Academy team for the mentorship, lab exercises, and structured curriculum.
