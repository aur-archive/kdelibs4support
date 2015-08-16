# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgname=kdelibs4support
pkgver=4.99.0
pkgrel=1
pkgdesc='KDE 4 Support'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/frameworks/kdelibs4support'
license=('LGPL')
depends=('kio' 'kunitconversion' 'kdesignerplugin' 'libsm')
makedepends=('extra-cmake-modules' 'kdoctools' 'qt5-tools')
groups=('kf5-aids')
replaces=('kde4support')
conflicts=('kde4support')
source=("http://download.kde.org/unstable/frameworks/${pkgver}/portingAids/${pkgname}-${pkgver}.tar.xz")
md5sums=('9470e1e6a391b702853aad225682b00c')

prepare() {
  mkdir -p build
}

build() {
  export XDG_DATA_DIRS="/opt/kf5/share:$XDG_DATA_DIRS"

  cd build
  cmake ../${pkgname}-${pkgver} \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/opt/kf5 \
    -DLIB_INSTALL_DIR=lib \
    -DBUILD_TESTING=OFF
#    -DSYSCONF_INSTALL_DIR=/etc
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
