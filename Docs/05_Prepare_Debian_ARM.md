# 05. Prepare Debian ARM Root Filesystem

## Download Minimal Debian RootFS

wget -c https://rcn-ee.com/rootfs/eewiki/minfs/debian-11.5-minimal-armhf-2022-10-06.tar.xz
sha256sum debian-11.5-minimal-armhf-2022-10-06.tar.xz
#sha256sum output:
0ea53b23483af4bcccca53f3fd907b5e404f2f607a6577d78e8c4daf5b869ad0  debian-11.5-minimal-armhf-2022-10-06.tar.xz

Verify the checksum matches the published value.

## Extract RootFS

tar xf debian-11.5-minimal-armhf-2022-10-06.tar.xz
