# 06. Prepare microSD Card

> **Warning:** Double-check your SD card device (e.g., `/dev/sdb`) to avoid data loss.

## Identify Card Device

lsblk
export DISK=/dev/sdb

## Wipe Partition Table

sudo dd if=/dev/zero of=${DISK} bs=1M count=8192 status=progress

## Install Bootloader (MLO and U-Boot)

sudo dd if=./u-boot/MLO of=${DISK} count=2 seek=1 bs=128k
sudo dd if=./u-boot/u-boot-dtb.img of=${DISK} count=4 seek=1 bs=384k

## Create Partition Table
check the version of sfdisk installed in your pc(sudo sfdisk --version)

#sfdisk >= 2.26.x
sudo sfdisk ${DISK} <<-EOF
4M,,L,*
EOF

text

## Format Partition (Disable ext4 features for U-Boot compatibility)

sudo mkfs.ext4 -L rootfs -O ^metadata_csum,^64bit ${DISK}1

## Mount Partition

sudo mkdir -p /media/rootfs
sudo mount ${DISK}1 /media/rootfs
