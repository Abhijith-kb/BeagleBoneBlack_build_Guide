# 02. Setup ARM Cross-Compiler

## Using Distro Toolchain

Most distros provide a suitable ARM cross-compiler:

sudo apt install gcc-arm-linux-gnueabi

## Using a Newer Toolchain

Download and extract a recent toolchain if needed:

wget -c https://mirrors.edge.kernel.org/pub/tools/crosstool/files/bin/x86_64/11.3.0/x86_64-gcc-11.3.0-nolibc-arm-linux-gnueabi.tar.xz
tar -xf x86_64-gcc-11.3.0-nolibc-arm-linux-gnueabi.tar.xz
export CROSS_COMPILE=$(pwd)/gcc-11.3.0-nolibc/arm-linux-gnueabi/bin/arm-linux-gnueabi-

## Verify the Toolchain

${CROSS_COMPILE}gcc --version

#Test Output:
arm-linux-gnueabi-gcc (GCC) 11.3.0
Copyright (C) 2021 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

