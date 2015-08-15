# Maintainer: Antonio Rojas <arojas@archlinux.org>

pkgname=bluedevil-frameworks-git
pkgver=r1477.b9b5f80
pkgrel=1
pkgdesc='KDE bluetooth framework'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/extragear/base/bluedevil'
license=('GPL2')
depends=('bluez' 'libbluedevil-frameworks-git' 'kio')
makedepends=('extra-cmake-modules' 'git')
provides=('bluedevil-frameworks')
conflicts=('bluedevil-frameworks' 'bluedevil')
install=$pkgname.install
source=("git://anongit.kde.org/bluedevil.git#branch=frameworks")
sha256sums=('SKIP')

pkgver() {
  cd bluedevil
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../bluedevil \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release \
    -DLIB_INSTALL_DIR=lib \
    -DLIBEXEC_INSTALL_DIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON
  make
}

package() {
  cd build
  make DESTDIR="$pkgdir" install
}
