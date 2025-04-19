# 03. Build U-Boot Bootloader

## Clone U-Boot Source

git clone -b v2022.04 https://github.com/u-boot/u-boot --depth=1
cd u-boot/

## Clean Previous Builds

make distclean CROSS_COMPILE=${CROSS_COMPILE}

## Configure for BeagleBone Black

make ARCH=arm CROSS_COMPILE=${CROSS_COMPILE} am335x_evm_defconfig

## Build U-Boot

make ARCH=arm CROSS_COMPILE=${CROSS_COMPILE}

## Outputs

- **MLO** (SPL/first-stage bootloader)  
- **u-boot.img** (second-stage bootloader)
