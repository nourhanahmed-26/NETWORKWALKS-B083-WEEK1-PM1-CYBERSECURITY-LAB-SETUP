# 🐉 Kali Linux on VirtualBox 

> Documentation of the network configuration and snapshot workflow for a fresh Kali Linux 

---

## ⚙️ Environment

| Component        | Detail                              |
|-------------------|--------------------------------------|
| 🖥️ Guest OS        | Kali GNU/Linux (Debian 64-bit)       |
| 🏷️ VM Name         | `kali-linux-2026.2-virtualbox-amd64` |
| 📦 Hypervisor      | Oracle VirtualBox                    |
| 🧠 Base Memory     | 8322 MB                              |
| 🧮 Processors      | 2                                    |
| 💾 Disk            | 80.09 GB (SATA)                      |
| 🌐 Network Mode    | NAT Network (`NatNetwork`)           |
| 🔌 Network Adapter | Intel PRO/1000 MT Desktop (82540EM)  |

---
# 🪜 Lab Setup Procedure


## Step 1. Install 7-Zip

7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a `.7z` archive.

**Tool:** 7-Zip

---

## Step 2. Install VirtualBox

VirtualBox was installed as the hypervisor.

---

## Step 3. Create the NAT Network

A dedicated NAT Network was created in VirtualBox.

Configuration:
Network Name: NatNetwork
IPv4 Prefix:  10.0.0.0/24
DHCP:         Enabled
IPv6:         Disabled

![](<img width="1920" height="1080" alt="Screenshot (401)" src="https://github.com/user-attachments/assets/c2759153-0d4d-454b-90ae-e2f1604dd4b0" />
)

A **NAT Network** was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

This will allow future attacker and target VMs to communicate within the lab.


---
## Step 4. Import Kali Linux

The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows:
![](<img width="1920" height="1080" alt="Screenshot (398)" src="https://github.com/user-attachments/assets/f75312ca-18c0-4db1-a2e8-f2e71027485c" />
)
A shared folder was also configured for transferring required files between the host operating system and the Kali VM.

---


# 🪜 INSIDE KALI LINUX


## 1️⃣ Boot

The VM boots into the standard GRUB menu for Kali GNU/Linux.

![Kali desktop running](images/08-desktop-running.jpeg)
)

---

## 2️⃣ Network adapter configuration

Adapter 1 is attached to a **NAT Network** (named `NatNetwork`) rather than plain NAT — this lets the VM reach the internet while keeping the option open to add more VMs to the same virtual network later. Promiscuous Mode is set to **Allow All**.

![Network adapter settings](<img width="1600" height="900" alt="WhatsApp Image 2026-09-10 at 11 23 56 PM (2)" src="https://github.com/user-attachments/assets/13be05f9-f9ca-4ea4-85f5-a191f435c824" />
)
The VM network adapter was configured as follows:

```text
Adapter 1
Attached to: NAT Network
Network:     NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop
```
---

## 3️⃣ Verifying the IP address

Desktop after boot, network active ✅:

![Kali desktop running](<img width="1448" height="1086" alt="WhatsApp Image 2026-09-10 at 11 20 29 PM" src="https://github.com/user-attachments/assets/ee9ade58-708f-461e-975b-bbb63655aef9" />
)

---

# 💡 What I Learned

Through this project, I learned how to create and configure a virtual environment for cybersecurity practice.

The most important concepts I picked up was:

### 1. NAT vs NAT Network

A standard NAT configuration and a NAT Network serve different purposes.

A NAT Network allows multiple VMs connected to the same virtual network to communicate with one another while providing network address translation for external connectivity.

### 2.Taking a snapshot 📸

Once networking was confirmed working, a snapshot was taken to preserve this known-good state before making further changes.

![snapshots](<img width="1448" height="1086" alt="WhatsApp Image 2026-09-10 at 11 20 36 PM" src="https://github.com/user-attachments/assets/250cc556-8952-428f-9d82-4221ab605a2a" />)




---

## 📝 Notes

- 🏷️ Snapshot name: `My Fresh Kali Linux after installation`
- 💬 Snapshot description: *"It is working good. I have set the IP address."*
- ⏪ Taking a snapshot here means any future misconfiguration (networking, dependencies, etc.) can be rolled back to this exact point instantly via **Snapshots → Restore** in VirtualBox Manager.
![snapshot](<img width="1600" height="900" alt="WhatsApp Image 2026-09-10 at 11 23 56 PM (5)" src="https://github.com/user-attachments/assets/3f435d8c-3ace-4a6e-aa70-1a84a14b99d1" />)
![snapshot](<img width="1600" height="900" alt="WhatsApp Image 2026-09-10 at 11 23 56 PM (4)" src="https://github.com/user-attachments/assets/5e813957-7ba7-4ec7-abec-c7e0a359ad64" />)


---



## 🔗 Tools & Resources

* 🗜️ **7-Zip:** [https://7-zip.org/download.html](https://7-zip.org/download.html)
* 📦**VirtualBox:** [https://virtualbox.org/wiki/Downloads](https://virtualbox.org/wiki/Downloads)
* 🐉 **Kali Linux:** [https://kali.org/get-kali](https://kali.org/get-kali)

---

## ✍️ Author

**Waqas Karim**

## 📌 Project Information

**Program Name:** Cybersecurity at Networkwalks | **Week:** 01 | **Project:** Cybersecurity & Pentesting Lab Setup | **Repository:** GitHub
