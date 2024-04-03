# Maintainer: Chaiwat Suttipongsakul <cwt@bashell.com>
pkgname="xf86-video-thead"
pkgver=r26.31abac5
pkgrel=1
pkgdesc="DDX for TH1520"
arch=('riscv64')
url="https://github.com/revyos/xf86-video-thead"
license=('MIT')
depends=('xorg-server')
makedepends=('xorg-server-devel' 'git')
source=("git+https://github.com/revyos/xf86-video-thead.git")
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$pkgname"
  printf 'r%s.%s' "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "$srcdir/$pkgname"
  git submodule init
  git submodule update
  ./autogen.sh
  ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir/$pkgname"
  make DESTDIR="$pkgdir/" install
}
