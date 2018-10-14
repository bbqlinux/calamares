# Maintainer: Daniel Hillenbrand <codeworkx [at] bbqlinux [dog] org>

pkgname=calamares
pkgver=3.2.2
pkgrel=1
pkgdesc='Distribution-independent installer framework'
arch=('i686' 'x86_64')
license=(GPL)
url="https://github.com/calamares"
license=('LGPL')
depends=('kconfig' 'kcoreaddons' 'kiconthemes' 'ki18n' 'kio' 'solid' 'yaml-cpp' 'kpmcore>=3.3.0'
         'boost-libs' 'ckbcomp' 'hwinfo' 'qt5-svg' 'polkit-qt5' 'gtk-update-icon-cache' 'pythonqt>=3.2' 'plasma-framework' 'libpwquality')
makedepends=('extra-cmake-modules' 'qt5-tools' 'qt5-translations' 'git' 'boost')
backup=('usr/share/calamares/modules/bootloader.conf'
        'usr/share/calamares/modules/displaymanager.conf'
        'usr/share/calamares/modules/initcpio.conf'
        'usr/share/calamares/modules/unpackfs.conf')

source+=("https://github.com/calamares/calamares/releases/download/v${pkgver}/calamares-${pkgver}.tar.gz")
sha256sums=('db04dbe4a577438ec59b61eeb7ab23421c291d86795064dc1c437d09aad81a92')

prepare() {
    cd ${srcdir}/calamares-${pkgver}
    # patches here
}

build() {
    cd ${srcdir}/calamares-${pkgver}

    mkdir -p build
    cd build
    cmake .. \
            -DCMAKE_BUILD_TYPE=Release \
            -DCMAKE_INSTALL_PREFIX=/usr \
            -DCMAKE_INSTALL_LIBDIR=lib \
            -DWITH_PYTHONQT:BOOL=ON \
            -DSKIP_MODULES="webview interactiveterminal initramfs \
                            initramfscfg dracut dracutlukscfg \
                            dummyprocess dummypython dummycpp \
                            dummypythonqt"
    make
}

package() {
    cd ${srcdir}/calamares-${pkgver}/build
    make DESTDIR="$pkgdir" install
}
