# $Id$
# Maintainer: Evangelos Foutras <evangelos@foutrelis.com>
# Contributor: tobias <tobias funnychar archlinux.org>

pkgname=xfce4-panel
pkgver=4.12.0
pkgrel=2
pkgdesc="Panel for the Xfce desktop environment"
arch=('i686' 'x86_64')
url="http://www.xfce.org/"
license=('GPL2')
groups=('xfce4')
depends=('exo' 'garcon' 'libxfce4ui' 'libwnck' 'hicolor-icon-theme'
         'desktop-file-utils')
makedepends=('intltool' 'gtk-doc')
source=(http://archive.xfce.org/src/xfce/$pkgname/${pkgver%.*}/$pkgname-$pkgver.tar.bz2)
sha256sums=('30920fc2e2fc26279a82b5261a155c2cc15ab2aa1ced2275684a6ff8261b97b0')

build() {
  cd "$srcdir/$pkgname-$pkgver"

  patch plugins/windowmenu/windowmenu.c ../../windowmenu.patch
  patch plugins/tasklist/tasklist-widget.c ../../tasklist-widget.patch

  ./configure \
    --prefix=/usr \
    --sysconfdir=/etc \
    --libexecdir=/usr/lib \
    --localstatedir=/var \
    --disable-static \
    --enable-gio-unix \
    --enable-gtk-doc \
    --enable-gtk3 \
    --disable-debug
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DESTDIR="$pkgdir" install
}

# vim:set ts=2 sw=2 et: