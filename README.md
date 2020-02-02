# clokworpi-kernel
List of patches to use when compiling linux kernel mainline

## Aplying patch
* git apply xxx.patch
replace "xxx" with patch name

## Compilation process:
### Copy clockworkpi defconfig to actual config
* cp ./arch/arm/configs/clockworkpi_cpi3_defconfig .config
### Edit your kernel, and save it
* make menuconfig
### Using cpi to compile
* make -j4
### Create u-boot image, remember to install u-boot-tools with: sudo apt-get install u-boot-tools
* mkimage -A arm -O linux -T kernel -C none -a 0x40008000 -e 0x40008000 -n "Linux kernel" -d arch/arm/boot/zImage uImage
* ckmod +x uImage

## Mount /boot if you don't have it populated
* sudo mount /dev/mmcblk0p1 /boot

## Create a backup for older kernel files just in case something goes wrong 
* sudo mv /boot/uImage /boot/uImage.bak
* sudo mv /boot/sun8i-r16-clockworkpi-cpi3.dtb /boot/sun8i-r16-clockworkpi-cpi3.dtb.bak
* sudo mv /boot/sun8i-r16-clockworkpi-cpi3-hdmi.dtb /boot/sun8i-r16-clockworkpi-cpi3-hdmi.dtb.bak
 
## Copy new files to /boot
* sudo mv uImage /boot
* sudo mv arch/arm/boot/dts/sun8i-r16-clockworkpi-cpi3.dtb /boot
* sudo mv arch/arm/boot/dts/sun8i-r16-clockworkpi-cpi3-hdmi.dtb /boot
