# $Id$
# Maintainer: Kyle Keen <keenerd@gmail.com>
# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Maintainer: Holmes <holmes_holmes [at] live [dot] com>

pkgname=jwm
pkgver=2.3.7
pkgrel=1
pkgdesc="A lightweight window manager for the X11 Window System"
arch=('i686' 'x86_64')
url="http://joewing.net/projects/jwm/"
license=('MIT')
depends=('libx11' 'libxft' 'libjpeg>=7' 'libxpm' 'libxinerama' 'libpng' 'cairo' 'librsvg')
backup=('etc/system.jwmrc')
source=(http://joewing.net/projects/jwm/releases/jwm-$pkgver.tar.xz
        jwm.desktop)
# contacted upstream about desktop
# no reply
md5sums=('95b297a89dedf45ef037c2596ad7d699'
         'ad898472f7538ffc3ff511c055fee535')

prepare() {
  cd "$srcdir/$pkgname-$pkgver"
  sed -i 's|/usr/local/share/|/usr/share/|' contrib/Makefile po/Makefile* example.jwmrc
}

build() {
  cd "$srcdir/$pkgname-$pkgver"
  ./configure --prefix=/usr --sysconfdir=/etc --disable-fribidi 
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make BINDIR="$pkgdir/usr/bin" MANDIR="$pkgdir/usr/share/man" \
       DESTDIR="$pkgdir" SYSCONF="$pkgdir/etc" install
  install -Dm644 "$srcdir/jwm.desktop" "$pkgdir/usr/share/xsessions/jwm.desktop"
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
