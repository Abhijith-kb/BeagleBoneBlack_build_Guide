# BeagleBone Black Bootstrapping Guide

This repository documents the complete process of building and booting U-Boot and the Linux kernel on the BeagleBone Black (Rev C), including preparing a Debian root filesystem and booting from a microSD card.

## Overview

- Cross-compile and build the bootloader (Das U-Boot)
- Compile the Linux kernel tailored for BeagleBone Black (Rev C)
- Prepare a minimal Debian ARM root filesystem
- Install and configure the system on a microSD card
- Boot and run a fully customized Linux environment on the BBB

---

## Features

- Step-by-step build and deployment instructions
- Images
- Troubleshooting and tips

---

## Directory Structure

- `docs/` – Detailed guides for each step
- `images/` – Diagrams and screenshots

---

## Quick Start

1. Review prerequisites in `docs/01_prerequisites.md`.
2. Follow the build and deployment steps in order.
3. Use provided scripts files as needed.

---

## Step-by-Step Procedure

### 1. Prepare Your Host Environment

- Use a recent version of Debian, Ubuntu, or Fedora on a 64-bit x86 PC (no virtualization).
- Install essential development tools.
- Ensure your shell is `bash`.

### 2. Set Up the ARM Cross Compiler

- Download and extract a pre-built ARM GCC cross-compiler from the official Kernel.org crosstool site.
- This toolchain allows building ARM binaries on your x86_64 machine.

### 3. Build the Bootloader (Das U-Boot)

- Clone the U-Boot source code from the official repository.
- Apply any BeagleBone Black-specific patches.
- Configure and compile U-Boot for the BBB hardware.
- Produce the `MLO` and `u-boot.img` files required for booting.

### 4. Compile the Linux Kernel

- Obtain kernel sources from the mainline Linux tree or a BBB-specific repository.
- Select the kernel version and configuration that matches your needs (including real-time support if required).
- Build the kernel image, device tree blobs, and kernel modules.

### 5. Prepare the Debian ARM Root Filesystem

- Download a minimal Debian ARM rootfs archive.
- This provides the basic user-space environment (including default users and passwords) for the BBB.

### 6. Set Up the microSD Card

- Identify your microSD card device.
- Erase existing partitions.
- Write the bootloader files to their required locations.
- Create a new Linux partition.
- Format the partition as `ext4`, ensuring compatibility with U-Boot by disabling certain features (like metadata checksums and 64-bit extensions).

### 7. Install the Kernel and Root Filesystem

- Mount the microSD card partition.
- Extract the Debian rootfs.
- Copy over the kernel image, device trees, and modules.
- Update the boot configuration to reference the correct kernel version.

### 8. Configure System Settings

- Edit system files to set up the filesystem table (`/etc/fstab`).
- Enable DHCP networking on the Ethernet interface for easy network access after boot.

### 9. Finalize and Boot

- Unmount the microSD card.
- Insert it into the BeagleBone Black.
- Power up the device to boot into your custom Linux system.

---
## Additional Points

### 1. Used Sources and Tools

1.1 **ARM Cross Compiler (GCC):**  
- Kernel.org Crosstool  
- Pre-built GCC toolchain for ARM (e.g., `x86_64-gcc-11.3.0-nolibc-arm-linux-gnueabi`)

1.2 **Bootloader (Das U-Boot):**  
- Official U-Boot Site  
- GitHub Source

1.3 **Linux Kernel:**  
- Mainline Kernel Source  
- BeagleBone Black-specific scripts: `bb-kernel`

1.4 **ARM Root Filesystem:**  
- Debian ARM  
- Minimal Debian ARM rootfs archives

1.5 **Learning Resources:**  
- [Fun with Beagle – Exploring the GPU](#)  
- [Fun with Beagle – GPU Video](#)

### 2. Boot Process Details

The BBB boot sequence starts with the ROM loading the **MLO** (first-stage bootloader), then **U-Boot**, which loads the kernel and device tree, and finally the root filesystem is mounted.

### 3. BeagleBone Black Booting Sequence

3.1 **Internal ROM Bootloader**  
When the BeagleBone Black powers on, the processor's internal ROM code runs first. It looks for the first-stage bootloader called **MLO** (Memory Loader or Secondary Program Loader) in a predefined boot device like eMMC or SD card.

3.2 **MLO (Memory Loader)**  
MLO initializes essential hardware, especially the external DRAM (RAM), since the internal ROM cannot access it. After initializing DRAM, MLO loads **U-Boot** into RAM and hands over control.

3.3 **U-Boot**  
U-Boot is a more capable bootloader that initializes additional hardware, sets up the boot environment, and loads the Linux kernel and device tree blob (DTB) into memory. It can also process configuration files like `uEnv.txt` to customize boot parameters.

3.4 **Linux Kernel**  
The kernel starts, initializes the rest of the hardware, detects attached devices, and mounts the root filesystem.

3.5 **Root Filesystem (RFS)**  
The root filesystem contains all user-space programs and data. Once mounted by the kernel, it provides the environment for users and applications to operate.

### 4. Filesystem Compatibility

U-Boot has limitations with newer ext4 features; ensure metadata checksums and 64-bit support are **disabled** during formatting for reliable booting.

### 5. Customization and Flexibility

Building from source allows you to enable or disable kernel features, add drivers, and tailor the root filesystem for your application.

### 6. Networking

The default configuration enables DHCP on Ethernet, making it straightforward to connect the BBB to a network after boot.

### 7. Backup and Recovery

It is recommended to back up bootloader files on the root filesystem for future recovery or flashing to eMMC.

### 8. Alternative Approaches

While this project uses manual source builds and Debian rootfs, alternatives like **Yocto** or **Buildroot** exist for automated image creation, though with less transparency and control.


---

## References

*   **Main Building Reference:** DigiKey Electronics. (n.d.). *Debian getting started with the beaglebone black*. DigiKey Forum. [https://forum.digikey.com/t/debian-getting-started-with-the-beaglebone-black/12967](https://forum.digikey.com/t/debian-getting-started-with-the-beaglebone-black/12967)
*   **Serial Console:** [Serial console]. YouTube, Retrieved from [https://www.youtube.com/watch?v=1a69sQZX3pQ](https://www.youtube.com/watch?v=1a69sQZX3pQ)

---

## Author

Abhijith K, 2025

