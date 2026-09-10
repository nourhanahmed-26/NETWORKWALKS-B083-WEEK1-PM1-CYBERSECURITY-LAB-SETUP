# NETWORKWALKS-B083-WEEK1-PM1-CYBERSECURITY-LAB-SETUP# Kali Linux on VirtualBox — Network & Snapshot Setup

Documentation of the network configuration and snapshot workflow for a fresh Kali Linux 2026.2 install running in Oracle VirtualBox.

## Environment

| Component        | Detail                              |
|-------------------|--------------------------------------|
| Guest OS          | Kali GNU/Linux (Debian 64-bit)       |
| VM Name           | `kali-linux-2026.2-virtualbox-amd64` |
| Hypervisor        | Oracle VirtualBox                    |
| Base Memory       | 8322 MB                              |
| Processors        | 2                                    |
| Disk              | 80.09 GB (SATA)                      |
| Network Mode      | NAT Network (`NatNetwork`)           |
| Network Adapter   | Intel PRO/1000 MT Desktop (82540EM)  |

## 1. Boot

The VM boots into the standard GRUB menu for Kali GNU/Linux.

![Boot menu](images/03-boot-menu.jpeg)

## 2. Network adapter configuration

Adapter 1 is attached to a **NAT Network** (named `NatNetwork`) rather than plain NAT, which allows the VM to reach the internet while keeping the option open to add more VMs to the same virtual network later. Promiscuous Mode is set to **Allow All**.

![Network adapter settings](images/04-network-adapter-settings.jpeg)

VM overview confirming the adapter and storage configuration:

![VM details overview](images/05-vm-details-overview.jpeg)

## 3. Verifying the IP address

Inside the guest, `ip a` confirms the interface is up and has picked up an address from the NAT network's DHCP:

\```
eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP
    link/ether 08:00:27:5a:87:bc brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.3/24 brd 10.0.0.255 scope global dynamic noprefixroute eth0
\```

![ip a output in terminal](images/01-network-config-ip-a.jpeg)

Desktop after boot, network active:

![Kali desktop running](images/08-desktop-running.jpeg)

## 4. Taking a snapshot

Once networking was confirmed working, a snapshot was taken to preserve this known-good state before making further changes.

Snapshot list before naming the first snapshot:

![Snapshot list, no snapshots yet](images/07-snapshot-list-before-naming.jpeg)

Snapshot dialog(s) — taken across multiple VirtualBox windows while testing:

![Multiple VirtualBox windows with snapshot dialog open](images/02-multi-window-snapshot-dialog.jpeg)

Resulting snapshot, named **"My Fresh Kali Linux after installation"**, with a description noting the working state and IP configuration:

![Snapshot with description](images/06-snapshot-with-description.jpeg)

## Notes

- Snapshot naming: `My Fresh Kali Linux after installation`
- Snapshot description: *"It is working good. I have set the IP address."*
- Taking a snapshot here means any future misconfiguration (networking, dependencies, etc.) can be rolled back to this exact point instantly via **Snapshots → Restore** in VirtualBox Manager.

## Repo structure

\```
.
├── README.md
└── images/
    ├── 01-network-config-ip-a.jpeg
    ├── 02-multi-window-snapshot-dialog.jpeg
    ├── 03-boot-menu.jpeg
    ├── 04-network-adapter-settings.jpeg
    ├── 05-vm-details-overview.jpeg
    ├── 06-snapshot-with-description.jpeg
    ├── 07-snapshot-list-before-naming.jpeg
    └── 08-desktop-running.jpeg
\```
