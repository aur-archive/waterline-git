# Maintainer:Vadim Ushakov < igeekless@gmail.com >
pkgname=waterline-git
pkgver=201507291345
pkgrel=1
pkgdesc="A lightweight framework for desktop widgets and applets"
arch=('i686' 'x86_64')
url="http://make-linux.org/"
license=('GPL')
depends=('alsa-lib' 'gtk2>=2.24.0' 'menu-cache' 'libsde-utils-git' 'libsde-utils-x11-git' 'libsde-utils-jansson-git' 'libsde-utils-gtk2-git' 'sde-reverse-meta-git')
optdepends=('libsmfm-gtk2-git')
makedepends=('automake' 'intltool' 'libtool' 'pkgconfig' 'git')
options=('!libtool')
provides=('waterline')
conflicts=('waterline')
source=('git+git://make-linux.org/sde/waterline.git')
md5sums=('SKIP')

_gitname="waterline"

pkgver() {
  date +%Y%m%d%H%M
}

build() {
  cd ${_gitname}

  msg "Starting make..."
  #####

  ./autogen.sh || return 1

  ./configure --prefix=/usr \
              --libexec=/usr/lib \
              --sysconfdir=/etc \
              --localstatedir=/var \
              --disable-static \
              --disable-maintainer-mode \
              --enable-silent-rules

  make || return 1
}

package() {
  cd ${_gitname}
  make DESTDIR=${pkgdir} install || return 1
}
