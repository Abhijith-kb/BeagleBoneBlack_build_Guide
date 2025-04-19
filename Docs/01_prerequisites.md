# 01. Prerequisites

## Hardware Requirements

- BeagleBone Black (Rev C)
- 8GB or larger microSD card
- mini USB (USB Mini-B) to USB Type-A cable (for serial console or power)
- Host PC running 64-bit Linux (Ubuntu recommended)

## Software Requirements

- Internet connection for downloading sources and packages

## Essential Packages

Install the following packages on your Linux host:

sudo apt update
sudo apt install build-essential bison flex swig git lzop libssl-dev gcc-arm-linux-gnueabi mkimage

- **build-essential, bison, flex, swig**: Required for building U-Boot and Linux kernel  
- **git**: Source code management  
- **lzop**: Kernel compression  
- **libssl-dev**: U-Boot cryptography  
- **gcc-arm-linux-gnueabi**: ARM cross-compiler  
- **mkimage**: U-Boot image creation  

## Additional Tools

- SD card reader/writer  
- Serial terminal software (e.g., putty, picocom, minicom, screen, GTKTerm)

