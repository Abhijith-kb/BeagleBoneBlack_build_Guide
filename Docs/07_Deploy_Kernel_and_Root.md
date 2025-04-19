# 07. Deploy Kernel and Root Filesystem

## Copy and paste kernel_version
export kernel_version=5.X.Y-Z

## Copy RootFS

sudo tar xfvp ./debian---armhf-/armhf-rootfs-.tar -C /media/rootfs/
sync

## Set uname_r in boot/uEnv.txt (can be done in next step - system configurations)

sudo sh -c "echo 'uname_r=${kernel_version}' >> /media/rootfs/boot/uEnv.txt"

## Copy Kernel Image

sudo cp -v ./kernelbuildscripts/deploy/${kernel_version}.zImage /media/rootfs/boot/vmlinuz-${kernel_version}

## Copy Device Tree binaries

sudo mkdir -p /media/rootfs/boot/dtbs/${kernel_version}/
sudo tar xfv ./kernelbuildscripts/deploy/${kernel_version}-dtbs.tar.gz -C /media/rootfs/boot/dtbs/${kernel_version}/

## Copy Kernel Modules

sudo tar xfv ./kernelbuildscripts/deploy/${kernel_version}-modules.tar.gz -C /media/rootfs/

