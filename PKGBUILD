# Maintainer: PrestonMa <pentie@gmail.com>
pkgname=lcd4linux-svn
pkgrel=2
pkgver=r1201
pkgdesc="Program that grabs information from the kernel and some subsystems and displays it on an external LCD"
arch=(i686 x86_64)
url="http://lcd4linux.bulix.org/"
license=('GPL')
groups=()
depends=(libusb-compat)
makedepends=('subversion')
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
noextract=()
md5sums=(SKIP)
builddepends=(autoconf libusb-compat libftdi serdisplib python2)
arch=(i686 x86_64)
backup=('etc/lcd4linux.conf')

_svnmod=lcd4linux
source=("$_svnmod::svn+https://ssl.bulix.org/svn/lcd4linux/trunk/")

pkgver() {
  cd "$srcdir/$_svnmod"
  local ver="$(svnversion)"
  printf "r%s" "${ver//[[:alpha:]]}"
}


build() {
  cd "$srcdir/$_svnmod"
  ./bootstrap
  PYTHON_VERSION=2 ./configure --prefix=/usr --with-drivers=all --with-python --with-x
  make
}

package() {
  cd "$srcdir/$_svnmod"
  make DESTDIR="$pkgdir/" install

  # install configuration file
  mkdir -p $pkgdir/etc
  install -m 0600 lcd4linux.conf.sample $pkgdir/etc/lcd4linux.conf
}

# vim:set ts=2 sw=2 et:


