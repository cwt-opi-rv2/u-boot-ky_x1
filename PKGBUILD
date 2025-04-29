# Maintainer: Chaiwat Suttipongsakul <cwt@bashell.com>

pkgname=u-boot-ky_x1
pkgver=2022.10
pkgrel=1
pkgdesc='Das U-Boot supports Ky X1 CPU'
_srcname=u-boot-orangepi-2022.10-ky
url="https://github.com/orangepi-xunlong/u-boot-orangepi/tree/v2022.10-ky"
arch=(riscv64)
license=('GPL-2.0+')
makedepends=(gcc swig uboot-tools dtc)
options=('!strip')
source=("${_srcname}.tar.gz::https://github.com/orangepi-xunlong/u-boot-orangepi/archive/refs/heads/v2022.10-ky.tar.gz"
        'config')

b2sums=('23902fed6f1ee0e2885a2d2cfb28613ed5e4b042c5d8e4e6c70fc5ac4bced41cd45e66d8834e8b05cc2d21f33c7125d95d0d82c1f4485628b38884393f164de6'
        'eb1a8bbd5145a2364179120c618f63e08e28790d143f58752853825aedc7ba137ae1c4d56b513d37d94840cb146b01ff7d9d2d6b228e978673f3e84c1d24a513')


prepare() {
  cd $_srcname
  cp ../../config .config
  make -j $(nproc) oldconfig
  cp .config ../../config.new
}

build() {
  cd $_srcname
  make -j $(nproc)
}

package() {
  cd $_srcname
  install -Dm644 bootinfo_emmc.bin "$pkgdir/usr/share/$pkgname/bootinfo_emmc.bin"
  install -Dm644 bootinfo_sd.bin "$pkgdir/usr/share/$pkgname/bootinfo_sd.bin"
  install -Dm644 bootinfo_spinand.bin "$pkgdir/usr/share/$pkgname/bootinfo_spinand.bin"
  install -Dm644 bootinfo_spinor.bin "$pkgdir/usr/share/$pkgname/bootinfo_spinor.bin"
  install -Dm644 FSBL.bin "$pkgdir/usr/share/$pkgname/FSBL.bin"
  install -Dm644 u-boot-env-default.bin "$pkgdir/usr/share/$pkgname/u-boot-env-default.bin"
  install -Dm644 u-boot-opensbi.itb "$pkgdir/usr/share/$pkgname/u-boot-opensbi.itb"
}

# vim:set ts=8 sts=2 sw=2 et:
