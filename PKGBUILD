# $Id: PKGBUILD 68133 2012-03-18 14:34:31Z lcarlier $
# Maintainer: Florian Pritz <flo@xssn.at>
# Contributor: Jan de Groot <jgc@archlinux.org>
# Contributor: Alexander Baldeck <alexander@archlinux.org>

_pkgbasename=libxss
pkgname=lib32-$_pkgbasename
pkgver=1.2.2
pkgrel=1
pkgdesc="X11 Screen Saver extension library (32-bit)"
arch=(x86_64)
license=('custom')
url="http://xorg.freedesktop.org/"
depends=('lib32-libxext' $_pkgbasename)
makedepends=('xorg-util-macros' gcc-multilib)
options=('!libtool')
source=(${url}/releases/individual/lib/libXScrnSaver-${pkgver}.tar.bz2)
sha1sums=('7b8298eec371c33a71232e3653370a98f03c6c88')

build() {
  export CC="gcc -m32"
  export CXX="g++ -m32"
  export PKG_CONFIG_PATH="/usr/lib32/pkgconfig"

  cd "${srcdir}/libXScrnSaver-${pkgver}"
  ./configure --prefix=/usr --sysconfdir=/etc \
    --libdir=/usr/lib32
  make
}

package() {
  cd "${srcdir}/libXScrnSaver-${pkgver}"

  make DESTDIR="${pkgdir}" install

  rm -rf "${pkgdir}"/usr/{include,share,bin}
  mkdir -p "$pkgdir/usr/share/licenses"
  ln -s $_pkgbasename "$pkgdir/usr/share/licenses/$pkgname"
}
