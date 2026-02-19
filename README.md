# VirtualBox Linux Lab on Mac mini (Late 2014)

![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)


This repository documents how to set up **Linux Mint**, **Ubuntu**, and **Kali Linux** as virtual machines using **VirtualBox** on a **Mac mini (Late 2014)**.

> Target hardware: Mac mini (Late 2014), Intel CPU, macOS (10.13+ recommended)  
> Hypervisor: Oracle VM VirtualBox

---

## Table of contents

- [1. Prerequisites](#1-prerequisites)
  - [1.1 Check Mac mini Hardware](#11-check-mac-mini-hardware)
  - [1.2 Install VirtualBox](#12-install-virtualbox)
  - [1.3 Download Linux ISOs](#13-download-linux-isos)

- [2. Common VirtualBox Configuration](#2-common-virtualbox-configuration)
  - [2.1 Create a New VM](#21-create-a-new-vm)
  - [2.2 Storage and ISO Attachment](#22-storage-and-iso-attachment)
  - [2.3 Network Settings](#23-network-settings)

- [3. Linux Mint VM Setup](#3-linux-mint-vm-setup)
  - [3.1 Recommended VM Settings](#31-recommended-vm-settings)
  - [3.2 Install Linux Mint](#32-install-linux-mint)
  - [3.3 Post‑Install Tweaks](#33-post-install-tweaks)

- [4. Ubuntu VM Setup](#4-ubuntu-vm-setup)
  - [4.1 Recommended VM Settings](#41-recommended-vm-settings)
  - [4.2 Install Ubuntu](#42-install-ubuntu)
  - [4.3 Post‑Install Tweaks](#43-post-install-tweaks)

- [5. Kali Linux VM Setup](#5-kali-linux-vm-setup)
  - [5.1 Recommended VM Settings](#51-recommended-vm-settings)
  - [5.2 Install Kali Linux](#52-install-kali-linux)
  - [5.3 Post‑Install Tweaks](#53-post-install-tweaks)

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
  ```

## 4. Ubuntu VM Setup

### 4.1 Recommended VM Settings

- **Name:** `Ubuntu-VM`
- **Type:** Linux
- **Version:** Ubuntu (64‑bit)
- **Base Memory:** 4096 MB (or more if available)
- **Processors:** 2–4 (depending on Mac mini resources)
- **Video Memory:** 128 MB
- **Graphics Controller:** VMSVGA
- **Storage:** 40–60 GB dynamically allocated VDI

### 4.2 Install Ubuntu

1. Start the `Ubuntu-VM` in VirtualBox.
2. Select **Try or Install Ubuntu**.
3. Choose **Install Ubuntu**.
4. Follow the installer prompts:
   - Keyboard layout
   - **Normal installation** (recommended)
   - Installation type: **Erase disk and install Ubuntu**  
     *(This only affects the virtual disk, not your Mac.)*
   - Timezone
   - Create your user account
5. When installation completes, click **Restart Now**.
6. When prompted, remove the ISO:
   - Devices → Optical Drives → Remove disk from virtual drive

### 4.3 Post‑Install Tweaks

Update the system:

```bash
sudo apt update && sudo apt upgrade -y
```

---

# ✅ **Kali Linux VM Setup 

## 5. Kali Linux VM Setup

### 5.1 Recommended VM Settings

- **Name:** `Kali-VM`
- **Type:** Linux
- **Version:** Debian (64‑bit) or Ubuntu (64‑bit)
- **Base Memory:** 4096–8192 MB
- **Processors:** 2–4
- **Video Memory:** 128 MB
- **Graphics Controller:** VMSVGA
- **Storage:** 40–60 GB dynamically allocated VDI

### 5.2 Install Kali Linux

1. Start the `Kali-VM`.
2. Select **Graphical Install**.
3. Complete the setup steps:
   - Language, location, keyboard
   - Network configuration (hostname, domain optional)
   - Create user and password
4. Partitioning:
   - Choose **Guided – use entire disk**
   - Confirm partition changes
5. Install the base system and tools.
6. When installation finishes, reboot and remove the ISO:
   - Devices → Optical Drives → Remove disk from virtual drive

### 5.3 Post‑Install Tweaks

Update Kali:

```bash
sudo apt update && sudo apt full-upgrade -y
```

