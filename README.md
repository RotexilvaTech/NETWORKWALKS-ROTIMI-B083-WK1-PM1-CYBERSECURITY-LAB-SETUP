<div align="center">

# 🔐 Cybersecurity Lab Environment Setup (NETWORKWALKS)

**Building an isolated virtual lab for penetration testing and ethical hacking practice**
</div>

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox%20v7.2-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.2-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/Windows%20OS-404040?style=flat-square&labelColor=C00000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/NetworkWalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Rotexilva%20Technology-C00000?style=flat-square" />
</p>

---

## 📌 Project Overview
This project focuses on setting up a **virtual cybersecurity and penetration-testing laboratory** using **VirtualBox**, **Kali Linux**, **Windows 10**, and **Wireshark**.

The lab provides a controlled environment where security tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and repeatably.

It runs on a **private virtual network**, so the Windows 10 and Android 9 machines can serve as targets for **authorized** security testing without exposing anything to the real network.

---

## 🎯 Objectives

The main objectives of this project are to:

- Install and configure VirtualBox
- Install/import Kali Linux as a virtual machine
- Create a private **NAT Network** for the cybersecurity lab
- Configure network connectivity for the Kali Linux VM
- Assign a consistent (static) IP address to the Kali VM
- Verify network connectivity and DNS resolution
- Take a clean VM snapshot for recovery
- Document the complete setup process
- Prepare the environment for future cybersecurity projects

  ---
  
  ## 🛡️ Purpose of the Lab

The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.

It can be used for activities such as:

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web security testing
- Exploitation practice
- Security-tool experimentation

  ---
  
## 🏗️ Lab Architecture
![](1-screenshot-title-image.png)

---

## ⚙️ Lab Configuration

| 🧩 Component       | ⚙️ Configuration   |
| ------------------ | ------------------  |
| 🖥️ Host OS         | Windows 11         |
| 🧠 Host RAM        | 12 GB               |
| ⚡ Processor       | Intel Core i5      |
| 🧰 Hypervisor      | VirtualBox 7.2    |
| 🐉 Security OS     | Kali Linux 2026.2  |
| 🧠 Kali RAM        | 2048 MB            |
| 🌐 Virtual Network | NAT Network        |
| 📡 Network Address | 10.0.0.0/24        |
| 🐧 Kali IP Address | 10.0.0.2/24        |
| 🚪 Default Gateway | 10.0.0.1           |
| 🌍 DNS Server      | 8.8.8.8            |
| 🔮 Future VM Range | 10.0.0.3–10.0.0.99 |

---

# 🪜 Lab Setup Procedure

## Task 1: Install 7-Zip

7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a `.7z` archive.
**Tool:** 7-Zip


##Task 2: Download and Install Oracle virtual Box
VirtualBox was installed as the hypervisor - choose mode (Expert mode) to have access to settings like Network.


## Task 3: Create the NAT Network
A dedicated NAT Network was created in VirtualBox.

Configuration:
Network Name: NatNetwork
IPv4 Prefix:  10.0.0.0/24
DHCP:         Enabled
IPv6:         Disabled

<img width="4032" height="3024" alt="20261119_233238" src="https://github.com/user-attachments/assets/164a1940-9c52-45d4-8903-42db6f27da9e" />

A **NAT Network** was selected because virtual machines connected to the same NAT Network can communicate with one another while still having outbound internet access (for updates, package installs, and DNS resolution).

This allows the Kali Linux attacker VM and the target VMs (Windows 11, Windows 10, Android 9, and any future machines) to communicate within the lab.

By default, systems outside the NAT Network cannot initiate connections to the VMs unless port forwarding is configured. This keeps vulnerable target machines isolated from the host LAN and the wider internet.


##Task 4: Import Kali Linux
The Kali Linux virtual machine was downloaded from the official Kali Linux website (kali.org) and imported into VirtualBox.

### Network adapter
| Setting | Value |
|---------|-------|
| Adapter | Adapter 1 |
| Attached to | NAT Network |
| Network name | `NatNetwork` |
| Adapter type | Intel PRO/1000 MT Desktop |

### VM resources
| Resource | Allocation |
|----------|-----------|
| RAM | 2048 MB |
| CPU | _N_ |
| Disk | _80GB_ |

<img width="3024" height="4032" alt="20261119_234000" src="https://github.com/user-attachments/assets/351ed37b-9278-461c-836f-31168b13d378" />


## Task 5: Configure the Kali Linux Network
The Kali Linux network configuration was checked and set to a consistent (static) IPv4 address.

| Setting | Value |
|---------|-------|
| IP address | `10.0.0.2` |
| Subnet mask | `255.255.255.0` (/24) |
| Gateway | `10.0.0.1` |
| DNS | `8.8.8.8` |

A consistent IP address makes the lab easier to document and lets the Kali machine be referenced reliably in future exercises.

### Configuration commands - setting up IP address. mask, gateway, and dns( I used 10.0.0.1 as my dns).
ipv4.method manual \
  ipv4.addresses 10.0.0.2/24 \
  ipv4.gateway 10.0.0.1 \
  ipv4.dns 10.0.0.1
  

<img width="3024" height="4032" alt="20261119_234345" src="https://github.com/user-attachments/assets/f6a14b9d-c257-4dc7-a0f5-75a1c27502b7" />

## Step 6: Check Kali Internet Access

Internet connectivity on the Kali VM was verified by opening a web browser and searching on Google.com. A successful search confirms that outbound traffic, DNS resolution, and HTTPS all work from inside the NAT Network.

### Procedure
1. Start the Kali Linux VM and log in.
2. Open the Firefox browser.
3. Go to `https://www.google.com`.
4. Run a test search and confirm the results load.

<img width="3024" height="4032" alt="20261119_234617" src="https://github.com/user-attachments/assets/6b128bda-562b-42ae-90bd-03b0e62636da" />

## Task 7: Create a Clean VM Snapshot

After completing the initial configuration, a VirtualBox snapshot was created.
snapshot name: FirstKaliworking - network

The snapshot represents the clean baseline of the laboratory.
If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.

# 🔎 Lab Verification

| ✅ Test                        | 🧾 Command                      | 🎯 Expected Result              |
| ----------------------------- | ------------------------------- | ------------------------------- |
| 🌐 Check IP address           | `ip a`                          | Correct Kali IP displayed       |
| 📡 Test gateway               | `ping 10.0.0.1`                 | Successful replies              |
| 🌍 Test Internet connectivity | `ping 8.8.8.8`                  | Successful replies              |
| 🔎 Test DNS resolution        | `nslookup networkwalks.com`     | Domain resolves                 |
| 🧰 Verify Nmap                | `nmap --version`                | Nmap version displayed          |
| 🔄 Verify snapshot            | Restore snapshot and run `ip a` | Baseline configuration restored |


# Extra Project: Windows 10 VM Environment

## Task 1: Windows 10 Lab Setup

The Windows 10 OS image was downloaded from Microsoft and a new virtual machine was created in VirtualBox, named **Windows 10 - Lab**. The OS image was then attached and installed.

### VM Resources
| Resource | Allocation |
|----------|-----------|
| VM name | Windows 10 - Lab |
| RAM | 4 GB |
| Drive | 45 GB |

![Windows 10 VM creation and installation](https://github.com/user-attachments/assets/7bb45ae2-c668-4028-9387-de33ad6705c4)

## Task 2: Set the Windows 10 VM Network

### Attach to the same NAT Network as Kali
The Windows 10 VM network adapter was attached to the same NAT Network as the Kali VM, so the two machines can communicate.

| Setting | Value |
|---------|-------|
| Adapter | Adapter 1 |
| Attached to | NAT Network |
| Network name | `NatNetwork` |

![Windows 10 VM network adapter settings](https://github.com/user-attachments/assets/7c2eabb6-a82f-4210-af7e-21fc93872129)

## Task 3: Configure a static IP address
The IP address, subnet mask, default gateway, and DNS server were set manually inside Windows.

| Setting | Value |
|---------|-------|
| IP address | `10.0.0.10` _(confirm)_ |
| Subnet mask | `255.255.255.0` (/24) |
| Default gateway | `10.0.0.1` _(confirm)_ |
| DNS | `8.8.8.8` _(confirm)_ |

![Windows 10 IPv4 settings](https://github.com/user-attachments/assets/a9bd1d66-637b-4860-b694-b6374e2fe45b)


## Task 4: Test Windows network access
Connectivity was tested by pinging the Kali VM and checking internet access from Windows.

### Test using command prompt
```cmd
ipconfig
ping 10.0.0.2
ping 8.8.8.8
```

![Windows 10 network test](https://github.com/user-attachments/assets/70358d54-c6d0-4c10-84a2-ef14317b2448)

## Task 5: Test Connectivity Between the VMs (Kali → Windows 10)
Connectivity from Kali to the Windows 10 VM was tested from the Kali terminal.

```bash
ping 10.0.0.10
```

![Kali to Windows 10 ping test](https://github.com/user-attachments/assets/e8ce4fd1-9981-4f3f-a4c4-723af2bc11e3)

# VM Lab Verification

| Test | Result |
|------|--------|
| Windows 10 → Kali | ✅ Success |
| Windows 10 → Internet | ✅ Success |
| Kali → Windows 10 | ✅ Success |


# 🐞 Problems Encountered & Solutions

An IP address conflict occurred during this step. It was identified and resolved  by _(changing IP address to an unused address)_.






