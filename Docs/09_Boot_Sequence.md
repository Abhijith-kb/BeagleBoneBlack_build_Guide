# 09. Boot Sequence

The BeagleBone Black boot process from microSD card proceeds as follows:

1. **Internal ROM Code Execution:**  
   The onboard ROM code initializes the processor and searches for a bootable device (microSD, eMMC, USB, UART) in a predefined order.

2. **Loading the Secondary Bootloader (MLO/SPL):**  
   The ROM loads the MLO (SPL - Secondary Program Loader) from the first partition of the microSD card into internal RAM and executes it.

3. **Loading and Executing the Primary Bootloader (U-Boot):**  
   SPL loads `u-boot-dtb.img` into RAM and transfers execution to it.

4. **Loading the Linux Kernel and Device Tree:**  
   U-Boot loads the Linux kernel (`vmlinuz-5.x.y-z`) and the device tree blob (/media/rootfs/boot/dtbs/${kernel_version}/) into RAM.

5. **Kernel Initialization and Transition to User Space:**  
   The kernel initializes hardware, mounts the root filesystem from the SD card, and starts user-space services.

