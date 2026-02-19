# VirtualBox Linux Lab on Mac mini (Late 2014)

This repository documents how to set up **Linux Mint**, **Ubuntu**, and **Kali Linux** as virtual machines using **VirtualBox** on a **Mac mini (Late 2014)**.

> Target hardware: Mac mini (Late 2014), Intel CPU, macOS (10.13+ recommended)  
> Hypervisor: Oracle VM VirtualBox

---

## Table of contents

- [1. Prerequisites](#1-prerequisites)
  - [1.1 Check Mac mini hardware](#11-check-mac-mini-hardware)
  - [1.2 Install VirtualBox](#12-install-virtualbox)
  - [1.3 Download Linux ISOs](#13-download-linux-isos)
- [2. Common VirtualBox configuration](#2-common-virtualbox-configuration)
  - [2.1 Create a new VM](#21-create-a-new-vm)
  - [2.2 Storage and ISO attachment](#22-storage-and-iso-attachment)
  - [2.3 Network settings](#23-network-settings)
- [3. Linux Mint VM setup](#3-linux-mint-vm-setup)
  - [3.1 Recommended VM settings](#31-recommended-vm-settings)
  - [3.2 Install Linux Mint](#32-install-linux-mint)
  - [3.3 Post‑install tweaks](#33-post-install-tweaks)
- [4. Ubuntu VM setup](#4-ubuntu-vm-setup)
  - [4.1 Recommended VM settings](#41-recommended-vm-settings)
  - [4.2 Install Ubuntu](#42-install-ubuntu)
  - [4.3 Post‑install tweaks](#43-post-install-tweaks)
- [5. Kali Linux VM setup](#5-kali-linux-vm-setup)
  - [5.1 Recommended VM settings](#51-recommended-vm-settings)
  - [5.2 Install Kali Linux](#52-install-kali-linux)
  - [5.3 Post‑install tweaks](#53-post-install-tweaks)
- [6. VirtualBox Guest Additions](#6-virtualbox-guest-additions)
- [7. Snapshots and backups](#7-snapshots-and-backups)
- [8. GitHub usage for this repo](#8-github-usage-for-this-repo)

---

## 1. Prerequisites

### 1.1 Check Mac mini hardware

- **Model:** Mac mini (Late 2014), Intel CPU.
- **RAM:** At least **8 GB** recommended (16 GB is ideal if you want multiple VMs running).
- **Disk space:** Aim for **100+ GB free** if you plan to keep all three VMs.

On macOS, check:

- **Apple menu → About This Mac** for RAM and storage.

### 1.2 Install VirtualBox

1. Go to the official VirtualBox website.
2. Download the **macOS** installer.
3. Run the `.dmg` and follow the installation steps.
4. If macOS blocks the extension:
   - Go to **System Preferences → Security & Privacy → General**.
   - Click **Allow** for Oracle America, then retry the install.

### 1.3 Download Linux ISOs

Download the latest stable ISOs:

- **Linux Mint:** Cinnamon edition ISO.
- **Ubuntu:** Desktop LTS ISO.
- **Kali Linux:** Installer or Live ISO (64‑bit).

Save them in a folder like `~/Downloads/isos/`.

---

## 2. Common VirtualBox configuration

These steps are similar for Mint, Ubuntu, and Kali; you’ll just change the ISO and VM name.

### 2.1 Create a new VM

1. Open **VirtualBox**.
2. Click **New**.
3. Set:
   - **Name:** e.g., `LinuxMint-VM`, `Ubuntu-VM`, `Kali-VM`.
   - **Type:** `Linux`.
   - **Version:** `Ubuntu (64-bit)` (works for Mint and Kali too on Intel Mac).
4. **Memory size:**
   - Mint: **2048–4096 MB**
   - Ubuntu: **4096 MB** (or more if you can)
   - Kali: **4096 MB** (or more for heavy tools)
5. **Hard disk:**
   - Choose **Create a virtual hard disk now**.
   - Type: **VDI**.
   - Storage: **Dynamically allocated**.
   - Size:
     - Mint: **30–40 GB**
     - Ubuntu: **40–60 GB**
     - Kali: **40–60 GB**

### 2.2 Storage and ISO attachment

1. Select the VM → **Settings → Storage**.
2. Under **Controller: IDE** or **SATA**, click the empty optical drive.
3. Click the disk icon → **Choose a disk file…**.
4. Select the appropriate ISO (Mint, Ubuntu, or Kali).
5. Click **OK**.

### 2.3 Network settings

For basic internet access:

1. VM → **Settings → Network**.
2. **Adapter 1:** Enable.
3. **Attached to:** `NAT` (simple and works out of the box).

Optional: use **Bridged Adapter** if you want the VM to appear as a separate device on your LAN.

---

## 3. Linux Mint VM setup

### 3.1 Recommended VM settings

- **Name:** `LinuxMint-VM`
- **Base memory:** 2048–4096 MB
- **Processors:** 2 (if your Mac mini has at least 4 cores)
- **Video memory:** 64–128 MB
- Enable **3D Acceleration** if performance is poor and Guest Additions are installed.

### 3.2 Install Linux Mint

1. Start the `LinuxMint-VM`.
2. In the boot menu, choose **Start Linux Mint**.
3. Once the live desktop loads, double‑click **Install Linux Mint**.
4. Follow the installer:
   - Language, keyboard layout.
   - **Installation type:** Erase disk (this only affects the virtual disk).
   - Timezone and user account.
5. When installation finishes, click **Restart Now** and remove the ISO when prompted.

### 3.3 Post‑install tweaks

After logging in:

- **Update system:**
  ```bash
  sudo apt update && sudo apt upgrade -y
