# Maintainer: Sebastien Luttringer <seblu+arch@seblu.net>

pkgname=cpupower
pkgver=3.1.2
pkgrel=1
pkgdesc="Linux kernel $pkgver cpupower tool"
license=('GPL2')
arch=('i686' 'x86_64')
url='http://www.kernel.org'
backup=('etc/conf.d/cpupower')
options=(!strip !buildflags)
conflicts=('cpufrequtils')
provides=("cpufrequtils=$pkgver")
source=(
  "http://ftp.kernel.org/pub/linux/kernel/v3.0/linux-$pkgver.tar.xz"
  'rc'
  'conf'
)
md5sums=('24027361d3ea6ea2cdd7bbdd2effe43f'
         'd8b119eff7dc1a2d655eb71a47fa6215'
         '218fd36a7957d3170ed8bd1a0be1f62f')

build() {
  cd linux-$pkgver/tools/power/cpupower
  make
}

package() {
  cd linux-$pkgver/tools/power/cpupower
  make \
    DESTDIR="$pkgdir" \
    INSTALL='/bin/install -c' \
    mandir='/usr/share/man' \
    docdir='/usr/share/doc/cpupower' \
    install install-man
  # install rc.d script
  install -D -m 755 "$srcdir/rc" "$pkgdir/etc/rc.d/cpupower"
  install -D -m 644 "$srcdir/conf" "$pkgdir/etc/conf.d/cpupower"
}

# vim:set ts=2 sw=2 ft=sh et:
