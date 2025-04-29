# Das U-Boot support for Ky X1 CPU

The files will be installed to `/usr/share/u-boot-ky_x1/` on the **filesystem**, not the MTD. Therefore, you will need to flash them to MTD (or eMMC or SD) yourself.

## Flashing Guide for MTD
1. Check your MTD partitions. They should look like this:
   ```bash
   $ cat /proc/mtd
   dev:    size   erasesize  name
   mtd0: 00010000 00001000 "bootinfo"
   mtd1: 00010000 00001000 "private"
   mtd2: 00040000 00001000 "fsbl"
   mtd3: 00010000 00001000 "env"
   mtd4: 00030000 00001000 "opensbi"
   mtd5: 00f60000 00001000 "uboot"
   ```
2. Flash them using `flashcp` from the `mtd-utils` package.
   ```bash
   $ cd /usr/share/u-boot-ky_x1/
   $ sudo flashcp bootinfo_spinor.bin /dev/mtd0
   $ sudo flashcp FSBL.bin /dev/mtd2
   $ sudo flashcp u-boot-env-default.bin /dev/mtd3
   $ sudo flashcp u-boot-opensbi.itb /dev/mtd5
   ```
   *Do not touch `/dev/mtd1` and `/dev/mtd4`.*

## Flashing Guide for SD
TBD.

## Flashing Guide for eMMC
TBD.
