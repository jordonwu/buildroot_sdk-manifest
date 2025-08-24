# 1. download and sync code
For 2025.05.x.xml manifest file
```
$ mkdir buildroot_sdk
$ cd buildroot_sdk
$ repo init -u git@github.com:jordonwu/buildroot_sdk-manifest.git -b main -m 2025.05.x.xml
$ repo sync -j8
```

For 2025.02.x.xml manifest file
```
$ mkdir linux_sdk
$ cd linux_sdk
$ repo init -u git@github.com:jordonwu/buildroot_sdk-manifest.git -b main -m 2025.02.x.xml
$ repo sync -j8
```

For 2024.11.x.xml manifest file
```
$ mkdir linux_sdk
$ cd linux_sdk
$ repo init -u git@github.com:jordonwu/buildroot_sdk-manifest.git -b main -m 2024.11.x.xml
$ repo sync -j8
```

For 2024.08.x.xml manifest file
```
$ mkdir linux_sdk
$ cd linux_sdk
$ repo init -u git@github.com:jordonwu/buildroot_sdk-manifest.git -b main -m 2024.08.x.xml
$ repo sync -j8
```

For 2024.02.x.xml manifest file
```
$ mkdir linux_sdk
$ cd linux_sdk
$ repo init -u git@github.com:jordonwu/buildroot_sdk-manifest.git -b main -m 2024.02.x.xml
$ repo sync -j8
```

# 2. For Rock 5b board build & flash

## 2.1 build image
```
$ cd linux_sdk
$ ./build_rock5b.sh

when build done, you will get below files list:

# ls output_rock5b/images/ -alh
total 250M
drwxr-xr-x 2 soc soc 4.0K 3月  14 16:39 .
drwxrwxr-x 6 soc soc 4.0K 3月  14 16:39 ..
-rwxr-xr-x 1 soc soc  275 3月  14 16:16 boot.scr
-rw-r--r-- 1 soc soc  16M 3月  14 16:39 boot.vfat
-rw-r--r-- 1 soc soc  30M 3月  14 16:36 Image
-rw-r--r-- 1 soc soc 9.9M 3月  14 16:36 Image.gz
-rw-r--r-- 1 soc soc  11M 3月  14 16:39 image.itb
-rw-r--r-- 1 soc soc 409K 3月  14 16:16 rk3588_bl31_v1.40.elf
-rw-r--r-- 1 soc soc  72K 3月  14 16:16 rk3588_ddr_lp4_2112MHz_lp5_2736MHz_v1.12.bin
-rwxr-xr-x 1 soc soc 246K 3月  14 16:36 rk3588-rock-5b.dtb
-rw-r--r-- 1 soc soc  746 3月  14 16:39 rock5b.its
-rw-r--r-- 1 soc soc 250M 3月  14 16:39 rootfs.ext2
lrwxrwxrwx 1 soc soc   11 3月  14 16:39 rootfs.ext4 -> rootfs.ext2
-rw-r--r-- 1 soc soc  53M 3月  14 16:39 rootfs.tar
-rw-r--r-- 1 soc soc 276M 3月  14 16:39 sdcard.img
-rw-r--r-- 1 soc soc 836K 3月  14 16:22 u-boot.bin
-rw-r--r-- 1 soc soc 9.1M 3月  14 16:22 u-boot-rockchip.bin
```

# 2.2 flash sdcard.img to TF Card
* 1. you can using balenaEtcher to flash sdcard.img to your TF card (recommended)
* 2. or you can using below linux dd command to flash sdcard.img to your TF card
```
$ sudo dd if=sdcard.img of=/dev/sd<partition> bs=1M conv=fsync  status=progress
```
