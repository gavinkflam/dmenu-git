# Maintainer:  Håvard Pettersson <mail@haavard.me>
# Contributor: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Bartłomiej Piotrowski <bpiotrowski@archlinux.org>
# Contributor: Thorsten Töpper <atsutane-tu@freethoughts.de>
# Contributor: Thayer Williams <thayer@archlinux.org>
# Contributor: Jeff 'codemac' Mickey <jeff@archlinux.org>

pkgname=dmenu-git
_pkgname=dmenu
pkgver=4.8
pkgrel=3
pkgdesc="A generic menu for X"
url="http://tools.suckless.org/dmenu/"
arch=('i686' 'x86_64')
license=('MIT')
depends=('sh' 'libxinerama' 'libxft')
makedepends=('git')
provides=(${_pkgname})
conflicts=(${_pkgname})
source=("git://git.suckless.org/${_pkgname}#tag=${pkgver}"
        'config.h')
sha256sums=('SKIP'
            'SKIP')

prepare() {
  cp config.h "${_pkgname}/config.h"
}

build(){
  cd $_pkgname
  patch -p1 < ${startdir}/patches/00-dmenu-fuzzymatch-4.8.diff
  patch -p1 < ${startdir}/patches/01-dmenu-fuzzymatch-case-insensitive-4.8.diff
  make X11INC='/usr/include/X11' X11LIB='/usr/lib/X11'
}

package() {
  cd $_pkgname
  make DESTDIR="${pkgdir}" PREFIX='/usr' install

  install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${_pkgname}/LICENSE"
}
