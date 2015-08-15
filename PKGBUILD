# Maintainer: Peter Ivanov <ivanovp@gmail.com>
# Based on dvb-usb-rtl2832u-arch, author DonVla <donvla@users.sourceforge.net>

pkgname=dvb-usb-rtl2838u-arch
_kernelname="-ARCH"
#_kernelname="-ck"
_kversion="3.1.5"
pkgver=1.1_${_kversion}
pkgrel=1
pkgdesc="Kernel module for the RTL2832U, RTL2836U and RTL2838U DVB-T USB2.0 devices"
arch=('i686' 'x86_64')
url="http://dev.ivanov.eu/projects/rtl2838/"
license=('GPL')
depends=("kernel-headers")
install="${pkgname}.install"
source=("dvb-usb-rtl2838u.tar.gz::http://dev.ivanov.eu/projects/rtl2838/dvb-usb-rtl2838u.tar.gz")
md5sums=('f767d22de33e4eb3de0effff7bba7bd7')
sha256sums=('2bd8bea9cda586ee5dcb2d48c4a1b3eeae7f6ce71166bcff5a74af835951e17e')

build() {
  local _KERNEL="${_kversion}-${pkgrel}${_kernelname}"
  # set KERNEL_VERSION
  sed -e  "s#KERNEL_VERSION=.*#KERNEL_VERSION=${_KERNEL}#g" -i "${startdir}/${install}"

  cd "${srcdir}/dvb-usb-rtl2832u"

  export KBUILD_SRC="/usr/src/linux-${_KERNEL}"
  export INSTALL_MOD_PATH="${pkgdir}"
  export INSTALL_MOD_DIR=kernel/drivers/media/dvb/dvb-usb
  make -C "${KBUILD_SRC}" M="$PWD" modules
  make -C "${KBUILD_SRC}" M="$PWD" modules_install
}

# vim:set ts=2 sw=2 et:
