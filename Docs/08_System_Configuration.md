# 08. System Configuration

## Set Kernel Version in uEnv.txt

already shown in previous step

## Configure fstab
If booting is done from SD card, add:
```
echo '/dev/sdb1 / auto errors=remount-ro 0 1' >> /media/rootfs/etc/fstab
```

## Configure Networking
Edit `/media/rootfs/etc/network/interfaces`: 
```
sudo nano /media/rootfs/etc/network/interfaces
```
add:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

## Remove microcSD/ SD card 
```
sync
sudo umount /media/rootfs
```
