# 04. Build the Linux Kernel

## Clone Kernel Source
```
git clone https://github.com/RobertCNelson/bb-kernel ./kernelbuildscripts
cd kernelbuildscripts/
```

## Checkout Stable Branch(For am33x-v5.15- Longterm 5.15.x)
```
git checkout origin/am33x-v5.15 -b tmp
```

## Build
```
./build_kernel.sh
```

## Outputs
- **kernelbuildscripts/deploy/5.15.y-z.zImage** - Kernel Image (y and z can be 177-bone)
- **kernelbuildscripts/deploy/5.15.y-z-dtbs.tar.gz** - Kernel device tree binaries 
- **kernelbuildscripts/deploy/5.15.y-z-modules.tar.gz** - Kernel modules
