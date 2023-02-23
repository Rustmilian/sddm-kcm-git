# Maintainer: Rustmilian <######[@]######[.]me>

pkgname=sddm-kcm-git
pkgver=5.27.80_r744.g0f6ca4b
pkgrel=1
pkgdesc='KDE Config Module for SDDM'
arch=($CARCH)
url='https://community.kde.org/Frameworks'
license=(GPL)
depends=('kcmutils')
makedepends=('git' 'clang' 'extra-cmake-modules' 'knewstuff' 'kxmlgui' 'kcoreaddons' 'kauth' 'kconfigwidgets' 'kio' 'karchive' 'kdeclarative')
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
source=("git+https://github.com/KDE/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
    _ver="$(grep -m1 'set(PROJECT_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_INSTALL_LIBDIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
